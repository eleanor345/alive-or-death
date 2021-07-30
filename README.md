# alive-or-death
class cell:
    def _init_(self):
        self._status='dead'
    def set_dead(self):
        self._status='dead'
    def set_alive(self):
        self._status='alive'
    def is_alive(self):
        if self._status=='alive':
            return True
        return False
    def get_print_character(self):
        if self.is_alive():
            return '0'
        return '*'
        
        
from cell import cell
from random import randint

class Board:
    def _init_(self,rows,columns):
        self._rows=rows
        self._columns=columns
        self._grid=[[cells() for column_cell in range(self._columns)] for row_cells in range(self.rows)]
        self._generate_board()
    def draw_board(self):
        print('\n'*10)
        print('printing board')
        for row in self._grid:
            for column in row:
                print(column.get_print_character(),end='')
                print()
    def _generate_board(self):
        for row in self._grid:
            for column in row:
                chance_number =randint(0,2)
                if chance_number ==1:
                    column.set_alive()
