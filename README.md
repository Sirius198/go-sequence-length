# go-sequence-length

package main

import (
	"fmt"
	"sort"
)

func sequenceLength(input []int) int {
	ctr := 0
	n := len(input)
	sort.Ints(input)

	max := input[0]
	for _, value := range input {
		if value > max {
			max = value
		}
	}

	maxLength := max
	if n > maxLength {
		maxLength = n
	}

	for i := 0; i < n && ctr <= maxLength; i++ {
		if input[i] >= ctr+1 {
			ctr++
		}
	}
	return ctr
}

func main() {
	input := []int{4, 12, 5, 4, 3, 5, 4, 3, 8}
	fmt.Println(sequenceLength(input))
}
