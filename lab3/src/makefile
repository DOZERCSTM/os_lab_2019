CC=gcc
CFLAGS=-I.


all : find_min_max sequential_min_max parallel_min_max ExecProgram

sequential_min_max : utils.o find_min_max.o utils.h find_min_max.h
	$(CC) -o sequential_min_max find_min_max.o utils.o sequential_min_max.c $(CFLAGS)

parallel_min_max : utils.o find_min_max.o utils.h find_min_max.h
	$(CC) -o parallel_min_max utils.o find_min_max.o parallel_min_max.c -lm $(CFLAGS)

ExecProgram: task5.c 
	$(CC) -o ExecProgram task5.c

utils.o : utils.h
	$(CC) -o utils.o -c utils.c $(CFLAGS)

find_min_max.o : utils.h find_min_max.h
	$(CC) -o find_min_max.o -c find_min_max.c $(CFLAGS)

find_min_max :find_min_max.c find_min_max.h sequential_min_max.c utils.c utils.h
	$(CC) -std=c99 -c find_min_max.c find_min_max.h sequential_min_max.c utils.c utils.h 
	$(CC) -std=c99 find_min_max.o sequential_min_max.o utils.o -o findminmax $(CFLAGS)


clean :
	rm utils.o find_min_max.o sequential_min_max parallel_min_max