target=	keene

obj=	keene.o

all: $(target)

%.o: %.c $(wildcard *.h) $(wildcard include/*.h)
	$(CC) $(CPPFLAGS) $(CFLAGS) -c $< -o $@

$(target): $(obj)
	$(CC) -fPIC $(CPPFLAGS) $(CFLAGS) $(obj) -o $@ -lusb -lm

clean:
	rm -f *.o $(target)
