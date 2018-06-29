### <a name="profiling-aspnet-mvc4-apps-can-lead-to-fatal-execution-engine-error"></a>Profilowanie aplikacji ASP.Net MVC4 może prowadzić do krytyczny błąd aparatu wykonywania

|   |   |
|---|---|
|Szczegóły|Używanie zestawów narzędzia NGEN/profile profilowania może ulec awarii PROFILOWANEGO aplikacji platformy ASP.NET MVC 4 przy uruchamianiu z "Wykonywania aparatu wyjątek krytyczny"|
|Sugestia|Tego problemu w programie .NET Framework 4.5.2. Alternatywnie profilera mogą uniknąć tego problemu, określając <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> w jego maski zdarzeń.|
|Zakres|Krawędź|
|Wersja|4.5|
|Typ|środowisko uruchomieniowe|

