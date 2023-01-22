AllParser.java

```
protected void setStartAndEndOfGraph(LocalDateTime nowStat) {
  if (startOfGraph == null) {
    startOfGraph = nowStat;
  }
  if (endOfGraph == null) {
    endOfGraph = nowStat;
  }

  if (nowStat.compareTo(startOfGraph) < 0) {
    startOfGraph = nowStat;
  }
  if (nowStat.compareTo(endOfGraph) > 0) {
    endOfGraph = nowStat;
  }

  // TimeRange -------------------------------------------------
  LocalDateTime graphTimeRangeStart = LocalDateTime.parse("08.04.2018 16:08:55", DateTimeFormatter.ofPattern("dd.MM.yyyy HH:mm:ss"));
  boolean isAfter = graphTimeRangeStart.isAfter(startOfGraph);
  if (isAfter) {
      startOfGraph = graphTimeRangeStart;
  }

  LocalDateTime graphTimeRangeEnd = LocalDateTime.parse("08.04.2018 16:09:35", DateTimeFormatter.ofPattern("dd.MM.yyyy HH:mm:ss"));
  boolean isBefore = graphTimeRangeEnd.isBefore(endOfGraph);
  if (isBefore) {
      endOfGraph = graphTimeRangeEnd;
  }
  // TimeRange -------------------------------------------------

}
```