CXX = g++
PACKAGES = clanCore-2.2 clanDisplay-2.2 clanApp-2.2 clanGL-2.2 clanGL1-2.2 clanSWRender-2.2 clanGUI-2.2 clanDatabase-2.2 clanSqlite-2.2
CXXFLAGS = `pkg-config --cflags $(PACKAGES)` -std=c++98 -Wall
LDLIBS = `pkg-config --libs $(PACKAGES)` 
SOURCES = main.cc towerdefensegame.cc gamestatemanager.cc gamestate.cc gameplaystate.cc camera.cc renderer.cc tower.cc mob.cc map.cc tile.cc common.cc wave.cc level.cc mobgenerator.cc player.cc menustate.cc towerstats.cc messagebox.cc projectile.cc loginstate.cc levelselectionstate.cc mobfactory.cc
OBJECTS = $(SOURCES:.cc=.o)
EXECUTABLE = td

all: $(EXECUTABLE)
debug: CXXFLAGS += -g  # -D_GLIBCXX_DEBUG (This switch causes problems)
debug: $(EXECUTABLE)

$(EXECUTABLE): $(OBJECTS)
	$(CXX) $(LDLIBS) $(OBJECTS) -pthread -o $@

.depend: depend

# $^ lists the prerequisites of the target
# g++ -MM lists the dependencies of the given
# input file.
depend: $(SOURCES)
	rm -f ./.depend
	$(CXX) $(CXXFLAGS) -MM $^>>./.depend;

clean:
	$(RM) $(OBJECTS) $(EXECUTABLE)
