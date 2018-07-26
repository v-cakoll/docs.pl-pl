### <a name="profiling-aspnet-mvc4-apps-can-lead-to-fatal-execution-engine-error"></a>Profilowanie aplikacji ASP.Net MVC4 może prowadzić do krytyczny błąd aparatu wykonywania

|   |   |
|---|---|
|Szczegóły|Profilery za pomocą zestawów NGEN/profile może ulec awarii aplikacji ASP.NET MVC4 profilowanych przy uruchamianiu z "Wykonywanie aparatu wyjątek krytyczny"|
|Sugestia|Ten problem został rozwiązany w .NET Framework 4.5.2. Alternatywnie program profilujący może uniknąć tego problemu, określając <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> w jego maski zdarzeń.|
|Zakres|Krawędź|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|

