SRC = src/parsers.c src/utils.c src/philo.c \
      src/inits.c src/routine.c src/monitor.c src/time.c

NAME = philo
OBJ = $(SRC:.c=.o)
CC = cc
RM = rm -rf
CFLAGS = -Wall -Wextra -Werror -lpthread
USER = kneves

Reset = \033[0m
G = \033[32m
R = \033[31m
Y = \033[33m
blink = \033[6;7;1;3m

all: $(NAME)

$(NAME): $(OBJ)
	@$(CC) $(CFLAGS) $(OBJ) -o $(NAME)
	@echo "$(G)"
	-@timeout 3 curl ascii.live/rick
	@echo "-------------------------------------------------------------------------------------"
	@echo "$(blink)$(G) ✅ $(NAME) successfully compiled $(Reset)"
	@echo "$(G)-------------------------------------------------------------------------------------$(Reset)"

val:
	valgrind --leak-check=full --track-origins=yes ./philo 3 300 100 100 3

hell:
	valgrind --tool=helgrind ./philo 4 310 200 100

normalclean:
	-@$(RM) $(OBJ)

clean:
	-@$(RM) $(OBJ)
	@echo "$(Y)-------------------------------------------------------------------------------------"
	@echo " 😉 Objects from the $(NAME) project have been removed"
	@echo "-------------------------------------------------------------------------------------$(Reset)"

fclean: normalclean
	@echo "$(R)"
	-@timeout 2 curl ascii.live/forrest
	@$(RM) $(NAME)
	@echo "-------------------------------------------------------------------------------------"
	@echo "$(blink)$(R) ❌ removed $(NAME) executable $(Reset)"
	@echo "$(R)-------------------------------------------------------------------------------------$(Reset)"

re: normalclean all

credit:
	@echo "made by: $(USER)"

.PHONY: all clean fclean re
