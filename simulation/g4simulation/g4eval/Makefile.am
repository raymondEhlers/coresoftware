##############################################
# please add new classes in alphabetical order

AUTOMAKE_OPTIONS = foreign

AM_CPPFLAGS = \
  -I$(includedir) \
  -I$(OFFLINE_MAIN)/include/eigen3 \
  -I$(OFFLINE_MAIN)/include \
  -I`root-config --incdir`

lib_LTLIBRARIES = \
   libg4eval.la

libg4eval_la_LDFLAGS = \
  -L$(libdir) \
  -L$(OFFLINE_MAIN)/lib

libg4eval_la_LIBADD = \
  -lcalo_io \
  -lCLHEP \
  -lfun4all \
  -lg4detectors_io \
  -lg4jets_io \
  -lg4vertex_io \
  -ltrackbase_historic_io \
  -ltrack_io \
  -ltpc_io \
  -lmvtx_io \
  -lintt_io \
  -lmicromegas_io \
  -lphg4hit

pkginclude_HEADERS = \
  BaseTruthEval.h \
  CaloEvalStack.h \
  CaloEvaluator.h \
  CaloRawClusterEval.h \
  CaloRawTowerEval.h \
  CaloTruthEval.h \
  EventEvaluator.h \
  JetEvalStack.h \
  JetEvaluator.h \
  JetRecoEval.h \
  JetTruthEval.h \
  MomentumEvaluator.h \
  PHG4DstCompressReco.h \
  PHG4DSTReader.h \
  SvtxEvalStack.h \
  SvtxEvaluator.h \
  SvtxHitEval.h \
  SvtxClusterEval.h \
  SvtxTrackEval.h \
  SvtxTruthEval.h \
  SvtxVertexEval.h
  
#TrackEvaluation.h \
#TrackEvaluationContainer.h

#ROOTDICTS = \
#  TrackEvaluationContainer_Dict.cc

#pcmdir = $(libdir)
#nobase_dist_pcm_DATA = \
#  TrackEvaluationContainer_Dict_rdict.pcm

libg4eval_la_SOURCES = \
  $(ROOTDICTS) \
  BaseTruthEval.cc \
  CaloEvalStack.cc \
  CaloTruthEval.cc \
  CaloRawTowerEval.cc \
  CaloRawClusterEval.cc \
  CaloEvaluator.cc \
  EventEvaluator.cc \
  JetEvalStack.cc \
  JetTruthEval.cc \
  JetRecoEval.cc \
  JetEvaluator.cc \
  MomentumEvaluator.cc \
  PHG4DSTReader.cc \
  PHG4DstCompressReco.cc \
  SvtxEvalStack.cc \
  SvtxTruthEval.cc \
  SvtxHitEval.cc \
  SvtxClusterEval.cc \
  SvtxTrackEval.cc \
  SvtxVertexEval.cc \
  SvtxEvaluator.cc

#  TrackEvaluation.cc \
#  TrackEvaluationContainer.cc

# Rule for generating table CINT dictionaries.
%_Dict.cc: %.h %LinkDef.h
	rootcint -f $@ @CINTDEFS@ $(DEFAULT_INCLUDES) $(AM_CPPFLAGS) $^

#just to get the dependency
%_Dict_rdict.pcm: %_Dict.cc ;

################################################
# linking tests

noinst_PROGRAMS = testexternals

BUILT_SOURCES = \
  testexternals.cc

testexternals_SOURCES = \
  testexternals.cc

testexternals_LDADD = \
  libg4eval.la

testexternals.cc:
	echo "//*** this is a generated file. Do not commit, do not edit" > $@
	echo "int main()" >> $@
	echo "{" >> $@
	echo "  return 0;" >> $@
	echo "}" >> $@

clean-local:
	rm -f *Dict* $(BUILT_SOURCES) *.pcm
