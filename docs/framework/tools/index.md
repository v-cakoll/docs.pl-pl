---
title: Narzędzia programu .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- command line, .NET Framework tools
- .NET Framework, tools
- tools [.NET Framework]
- running .NET Framework tools
ms.assetid: a2ca532d-91f7-426a-9303-417c2ee1247c
ms.openlocfilehash: 60a9cb241f289cacc7437174f112114e843aca47
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645563"
---
# <a name="net-framework-tools"></a>Narzędzia programu .NET Framework

Narzędzia programu .NET Framework ułatwiają tworzenie i wdrażanie aplikacji oraz składników współpracujących z programem .NET Framework oraz zarządzanie nimi.

Większość narzędzi programu .NET Framework, które są opisane w tej sekcji, jest automatycznie instalowana z programem Visual Studio. Aby pobrać program Visual Studio, odwiedź stronę [Pobieranie programu Visual Studio.](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)

Można uruchomić wszystkie narzędzia z wiersza polecenia, z wyjątkiem Przeglądarki pamięci podręcznej zestawu (*Shfusion.dll*). Musisz uzyskać dostęp do *pliku Shfusion.dll* z Eksploratora plików.
  
Najlepszym sposobem uruchamiania narzędzi wiersza polecenia jest używanie wiersza polecenia dla deweloperów w programie Visual Studio. Te funkcje umożliwiają łatwe uruchamianie narzędzi bez przechodzenia do folderu instalacji. Aby uzyskać więcej informacji, zobacz [Wiersze poleceń](developer-command-prompt-for-vs.md).

> [!NOTE]
> Niektóre narzędzia są właściwe dla komputerów 32- lub 64-bitowych. Należy pamiętać, aby uruchomić wersję narzędzia odpowiednią dla swojego komputera.

## <a name="in-this-section"></a>W tej sekcji

- [Al.exe (Łącznik montażowy)](al-exe-assembly-linker.md)  
Generuje plik z manifestem zestawu z modułów lub plików zasobów.

- [Aximp.exe (importer kontroli Windows Forms ActiveX)](aximp-exe-windows-forms-activex-control-importer.md)  
Konwertuje definicje typów w bibliotece typów modelu COM dla formantu ActiveX do formantu Windows Forms.

- [Caspol.exe (narzędzie zasad zabezpieczeń dostępu do kodu)](caspol-exe-code-access-security-policy-tool.md)  
Umożliwia wyświetlanie i konfigurowanie zasad zabezpieczeń na poziomie zasad komputera, poziomie zasad użytkownika i poziomie zasad przedsiębiorstwa. W programie .NET Framework 4 i nowszych narzędzia nie ma wpływu na zasady zabezpieczeń dostępu do `true`kodu (CAS), chyba że [ \<legacyCasPolicy> element](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) jest ustawiony na . Aby uzyskać więcej informacji, zobacz [Zmiany zabezpieczeń](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes).

- [Cert2spc.exe (narzędzie do testowania certyfikatów wydawcy oprogramowania)](cert2spc-exe-software-publisher-certificate-test-tool.md)  
Tworzy certyfikat wydawcy oprogramowania (SPC) na podstawie co najmniej jednego certyfikatu X.509. To narzędzie jest przeznaczone wyłącznie do celów testowych.

- [Certmgr.exe (narzędzie Menedżera certyfikatów)](certmgr-exe-certificate-manager-tool.md)  
Zarządza certyfikatami, listami zaufania certyfikatów (CTL) i listami odwołania certyfikatów (CRL).

- [Program Clrver.exe (narzędzie wersji CLR)](clrver-exe-clr-version-tool.md)  
Raportuje wszystkie zainstalowane wersje środowiska wykonawczego języka wspólnego (CLR) na komputerze.

- [Wiersze poleceń](developer-command-prompt-for-vs.md)  
Umożliwia łatwiejsze korzystanie z narzędzi programu .NET Framework. Jest to wiersz polecenia, który automatycznie ustawia określone zmienne środowiskowe.

- [CorFlags.exe (Narzędzie do konwersji CorFlags)](corflags-exe-corflags-conversion-tool.md)  
Pozwala skonfigurować sekcję CorFlags w nagłówku obrazu przenośnego pliku wykonywalnego (PE).

- [Fuslogvw.exe (przeglądarka dzienników wiązania zestawu)](fuslogvw-exe-assembly-binding-log-viewer.md)  
Wyświetla informacji o powiązaniach zestawu pomagające ustalić, dlaczego program .NET Framework nie może zlokalizować zestawu w czasie wykonywania.

- [Gacutil.exe (narzędzie globalnej pamięci podręcznej zestawów)](gacutil-exe-gac-tool.md)  
Pozwala wyświetlać i manipulować zawartością globalnej pamięci podręcznej zestawów i pamięci podręcznej pobierania.

- [Ilasm.exe (monter IL)](ilasm-exe-il-assembler.md)  
Generuje przenośny plik wykonywalny (PE) z języka pośredniego (IL). Możesz uruchomić wynikowy plik wykonywalny, aby określić, czy IL działa zgodnie z oczekiwaniami.

- [Ildasm.exe (IL Disassembler)](ildasm-exe-il-disassembler.md)  
Pobiera przenośny plik wykonywalny (PE), który zawiera kod języka pośredniego (IL) i tworzy z niego plik tekstowy, który może być użyty jako wejście do asemblera IL (Ilasm.exe).

- [Installutil.exe (narzędzie instalatora)](installutil-exe-installer-tool.md)  
Umożliwia instalowanie i odinstalowywanie zasobów serwera przez wykonywanie składników instalatora w określonym zestawie. (Działa z klasami <xref:System.Configuration.Install> w obszarze nazw).

- [Lc.exe (Kompilator licencji)](lc-exe-license-compiler.md)  
Odczytuje pliki tekstowe zawierające informacje licencyjne i tworzy plik *.licenses,* który może być osadzony w pliku wykonywalnym środowiska wykonawczego języka wspólnego jako zasób.

- [Mage.exe (narzędzie do generowania manifestów i edycji)](mage-exe-manifest-generation-and-editing-tool.md)  
Umożliwia tworzenie, edytowanie i podpisywanie manifestów aplikacji i wdrożenia. Jako narzędzie wiersza polecenia *mage.exe* można uruchamiać zarówno ze skryptów wsadowych, jak i innych aplikacji opartych na systemie Windows, w tym ASP.NET aplikacji.

- [MageUI.exe (narzędzie do generowania manifestu i edycji, klient graficzny)](mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)  
Obsługuje taką samą funkcjonalność jak narzędzie wiersza polecenia Mage.exe, ale używa interfejsu użytkownika (UI) opartego na systemie Windows. Obsługuje te same funkcje co narzędzie wiersza polecenia *Mage.exe*, ale używa interfejsu użytkownika opartego na systemie Windows.

- [Program MDbg.exe (debuger wiersza polecenia framework framework)](mdbg-exe.md)  
Ułatwia dostawcom narzędzi i deweloperom aplikacji znajdowanie i usuwanie błędów w programach, których platformą docelową jest środowisko uruchomieniowe języka wspólnego programu .NET Framework. To narzędzie używa interfejsu API debugowania środowiska uruchomieniowego w celu dostarczania usług debugowania.

- [Mgmtclassgen.exe (Zarządzanie silnie typed Class Generator)](mgmtclassgen-exe.md)  
Umożliwia generowanie klasy zarządzanej wcześnie wiązanej dla określonej klasy Instrumentacji zarządzania Windows (WMI, Windows Management Instrumentation).

- [Mpgo.exe (narzędzie optymalizacji z przewodnikiem profilu zarządzanego)](mpgo-exe-managed-profile-guided-optimization-tool.md)  
Umożliwia dostrojenie zestawów obrazów natywnych przy użyciu typowych scenariuszy użytkownika końcowego. Mpgo.exe pozwala generować i zużywać dane profilu dla zestawu aplikacji obrazów natywnych (ale nie zestawów .NET Framework) przy użyciu scenariuszy szkoleniowych wybranych przez dewelopera aplikacji.

- [Ngen.exe (Generator obrazu natywnego)](ngen-exe-native-image-generator.md)  
Zwiększa wydajność zarządzanych aplikacji przez użycie obrazów natywnych (plików zawierających skompilowany kod maszynowy specyficzny dla danego procesora). Środowisko uruchomieniowe może używać obrazów natywnych z tej pamięci podręcznej, zamiast używać kompilatora JIT (Just-In-Time) w celu skompilowania oryginalnego zestawu.

- [Plik Peverify.exe (narzędzie PEVerify Tool)](peverify-exe-peverify-tool.md)  
Pomaga w sprawdzaniu, czy kod w języku Microsoft Intermediate Language (MSIL) oraz skojarzone z nim metadane spełniają wymagania dotyczące bezpieczeństwa typów.

- [Regasm.exe (narzędzie rejestracji zestawu)](regasm-exe-assembly-registration-tool.md)  
Odczytuje metadane w zestawie i dodaje niezbędne wpisy do rejestru. Umożliwia wyświetlane klientów COM jako klas .NET Framework.

- [Regsvcs.exe (narzędzie instalacyjne usług.NET)](regsvcs-exe-net-services-installation-tool.md)  
Ładuje i rejestruje zestaw, generuje i instaluje bibliotekę typów w określonej aplikacji COM+ w wersji 1.0 i konfiguruje usługi, które zostały dodane programowo do klasy.

- [Program Resgen.exe (generator plików zasobów)](resgen-exe-resource-file-generator.md)  
Konwertuje pliki tekstowe (*.txt* lub *.restext*) i pliki formatu zasobów opartego na języku XML *(.resx)* na pliki binarne środowiska wykonawczego wspólnego języka (*.resources*), które mogą być osadzone w pliku wykonywalnym binarnym w czasie wykonywania lub kompilowane w zestawy satelitarne.

- [Program SecAnnotate.exe (narzędzie annotatora zabezpieczeń.NET)](secannotate-exe-net-security-annotator-tool.md)  
Identyfikuje `SecurityCritical` i `SecuritySafeCritical` części złożenia.

- [SignTool.exe (narzędzie Podpisywanie)](signtool-exe.md)  
Podpisuje cyfrowo pliki, weryfikuje podpisy w plikach oraz oznacza pliki znacznikami czasu.

- [Sn.exe (narzędzie silnej nazwy)](sn-exe-strong-name-tool.md)  
Pomaga tworzyć zestawy o silnych nazwach. To narzędzie dostarcza opcje do zarządzania kluczami oraz generowania podpisów i weryfikowania ich.

- [SOS.dll (rozszerzenie debugowania SOS)](sos-dll-sos-debugging-extension.md)  
Ułatwia debugowanie programów zarządzanych w debugerze WinDbg.exe i programie Visual Studio, dostarczając informacje na temat wewnętrznego środowiska uruchomieniowego języka wspólnego.

- [SqlMetal.exe (narzędzie do generowania kodu)](sqlmetal-exe-code-generation-tool.md)  
Generuje kod i mapowanie dla składnika LINQ to SQL platformy .NET Framework.

- [Plik Storeadm.exe (narzędzie do przechowywania izolowanego)](storeadm-exe-isolated-storage-tool.md)  
Zarządza izolowanym magazynem; dostarcza opcje na potrzeby wyświetlania listy magazynów użytkownika i usuwania ich.

- [Tlbexp.exe (Eksporter biblioteki typów)](tlbexp-exe-type-library-exporter.md)  
Generuje bibliotekę typów opisującą typy, które są zdefiniowane w zestawie środowiska uruchomieniowego języka wspólnego.

- [Tlbimp.exe (importer biblioteki typów)](tlbimp-exe-type-library-importer.md)  
Konwertuje definicje typów znalezione w bibliotece typów modelu COM do równoważnych definicji w zestawie środowiska uruchomieniowego języka wspólnego.

- [Program Winmdexp.exe (narzędzie do eksportowania metadanych środowiska wykonawczego systemu Windows)](winmdexp-exe-windows-runtime-metadata-export-tool.md)  
Eksportuje zestaw .NET Framework, który jest kompilowany jako plik *.winmdobj* do składnika środowiska wykonawczego systemu Windows, który jest pakowany jako plik *.winmd,* który zawiera zarówno metadane środowiska wykonawczego systemu Windows, jak i informacje o implementacji.

- [Program Winres.exe (Edytor zasobów formularzy systemu Windows)](winres-exe-windows-forms-resource-editor.md)  
Pomaga zlokalizować zasoby interfejsu użytkownika *(.resx* lub *.resources* files), które są używane przez formularze systemu Windows. Można tłumaczyć ciągi, a następnie zmieniać rozmiar, przenosić i ukrywać kontrolki, aby pomieścić zlokalizowane ciągi.

## <a name="related-sections"></a>Powiązane sekcje

- [Narzędzia WPF](https://docs.microsoft.com/previous-versions/ms742404(v=vs.110))  
Zawiera narzędzia, takie jak narzędzie isXPS Conformance (isXPS.exe) i narzędzia do profilowania wydajności.

- [Narzędzia programu Windows Communication Foundation](../wcf/tools.md)  
Zawiera narzędzia, które ułatwiają tworzenie, wdrażanie i zarządzanie aplikacjami Windows Communication Foundation (WCF).
