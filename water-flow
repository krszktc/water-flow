island = """ 
1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1
1 1 1 1 1 0 1 1 1 1 1 1 1 1 1 1 1 1 1 1
1 1 0 0 0 0 1 0 0 0 0 0 1 1 1 1 1 0 0 0
0 0 0 1 1 0 0 0 1 1 1 1 1 1 1 1 1 0 1 1
1 1 0 1 1 0 1 0 0 1 1 1 1 1 1 1 0 0 0 0
1 1 1 1 1 1 1 0 0 1 1 1 0 1 1 1 0 0 1 1
1 0 1 0 1 1 1 1 1 1 0 0 0 1 1 1 1 0 1 1
0 0 0 0 1 1 0 0 1 1 0 0 0 0 0 1 1 1 1 1
1 0 0 0 1 1 1 0 0 1 1 1 1 0 0 1 1 1 1 1
1 1 0 0 1 1 1 0 0 1 1 1 1 1 0 1 1 1 1 1
1 1 1 0 1 1 1 1 1 1 1 1 1 1 0 1 1 1 1 1
"""

def calculate_flow(area):
    # prepare input for calculations
    row_list = []
    counter = 0
    for row in area.split("\n"):
        strip_row = row.strip().replace(" ","")
        if strip_row != "":
            row_list.append(list(strip_row))
    # find wholes around where water can get inside
    list_end_index = len(row_list)-1
    row_end_index = len(row_list[0])-1
    for row in row_list:
        row_index = row_list.index(row)
        if row_index == 0 or row_index == list_end_index:
            for el in row:
                if el == "0":
                    row[row.index(el)] = "w"
                    counter += 1
        else:
            if row[0] == "0":
                row[0] = "w"
                counter += 1
            if row[row_end_index] == "0":
                row[row_end_index] = "w"
                counter += 1
    # calculate water flow
    list_begin = 1
    while list_begin < list_end_index:
        row_el_begin = 1
        while row_el_begin < row_end_index:
            if row_list[list_begin][row_el_begin] == "0":
                if (row_list[list_begin-1][row_el_begin] == "w" or
                        row_list[list_begin+1][row_el_begin] == "w" or
                        row_list[list_begin][row_el_begin-1] == "w" or
                        row_list[list_begin][row_el_begin+1] == "w"):
                    while row_list[list_begin-1][row_el_begin] == "0":
                        list_begin -= 1
                    while row_list[list_begin][row_el_begin-1] == "0":
                        row_el_begin -= 1
                    row_list[list_begin][row_el_begin] = "w"
                    counter += 1
            row_el_begin += 1
        list_begin += 1
    # show results
    island_size = len(row_list) * len(row_list[0])
    print("Island size is {}".format(island_size))
    print("Dry island area is {}".format(island_size - counter))
    print("Water is in {} places".format(counter))
    for el in row_list:
        print(" ".join(el))

calculate_flow(island)