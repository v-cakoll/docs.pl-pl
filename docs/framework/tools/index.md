---
title: Narzędzia programu .NET Framework
description: Zapoznaj się z listą narzędzi platformy .NET, które ułatwiają tworzenie i wdrażanie aplikacji oraz składników przeznaczonych dla platformy .NET oraz zarządzanie nimi.
ms.date: 03/30/2017
helpviewer_keywords:
- command line, .NET Framework tools
- .NET Framework, tools
- tools [.NET Framework]
- running .NET Framework tools
ms.assetid: a2ca532d-91f7-426a-9303-417c2ee1247c
ms.openlocfilehash: 0a5cbcd4fa60b819d3ab07a4f221e77ca106c321
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166849"
---
# <a name="net-framework-tools"></a>Narzędzia programu .NET Framework

Narzędzia programu .NET Framework ułatwiają tworzenie i wdrażanie aplikacji oraz składników współpracujących z programem .NET Framework oraz zarządzanie nimi.

Większość narzędzi programu .NET Framework, które są opisane w tej sekcji, jest automatycznie instalowana z programem Visual Studio. Aby pobrać program Visual Studio, odwiedź stronę [pliki do pobrania programu Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) .

Można uruchomić wszystkie narzędzia z wiersza polecenia, z wyjątkiem podglądu pamięci podręcznej zestawów (*Shfusion.dll*). Musisz uzyskać dostęp do *Shfusion.dll* z Eksploratora plików.
  
Najlepszym sposobem uruchamiania narzędzi wiersza polecenia jest używanie wiersza polecenia dla deweloperów w programie Visual Studio. Te funkcje umożliwiają łatwe uruchamianie narzędzi bez przechodzenia do folderu instalacji. Aby uzyskać więcej informacji, zobacz [wiersza polecenia](developer-command-prompt-for-vs.md).

> [!NOTE]
> Niektóre narzędzia są właściwe dla komputerów 32- lub 64-bitowych. Należy pamiętać, aby uruchomić wersję narzędzia odpowiednią dla swojego komputera.

## <a name="in-this-section"></a>W tej sekcji

- [Al.exe (Konsolidator zestawu)](al-exe-assembly-linker.md)  
Generuje plik z manifestem zestawu z modułów lub plików zasobów.

- [Aximp.exe (Windows Forms importer formantów ActiveX)](aximp-exe-windows-forms-activex-control-importer.md)  
Konwertuje definicje typów w bibliotece typów modelu COM dla formantu ActiveX do formantu Windows Forms.

- [Caspol.exe (Narzędzie zasad zabezpieczeń dostępu kodu)](caspol-exe-code-access-security-policy-tool.md)  
Umożliwia wyświetlanie i konfigurowanie zasad zabezpieczeń na poziomie zasad komputera, poziomie zasad użytkownika i poziomie zasad przedsiębiorstwa. W .NET Framework 4 i nowszych tego narzędzia nie wpływa na zasady zabezpieczeń dostępu kodu (CAS), chyba że [ \<legacyCasPolicy> element](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) jest ustawiony na `true` . Aby uzyskać więcej informacji, zobacz [zmiany zabezpieczeń](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes).

- [Cert2spc.exe (Narzędzie testowe certyfikatów wydawców oprogramowania)](cert2spc-exe-software-publisher-certificate-test-tool.md)  
Tworzy certyfikat wydawcy oprogramowania (SPC) na podstawie co najmniej jednego certyfikatu X.509. To narzędzie jest przeznaczone wyłącznie do celów testowych.

- [Certmgr.exe (narzędzie Menedżer certyfikatów)](certmgr-exe-certificate-manager-tool.md)  
Zarządza certyfikatami, listami zaufania certyfikatów (CTL) i listami odwołania certyfikatów (CRL).

- [Clrver.exe (Narzędzie wersji środowiska CLR)](clrver-exe-clr-version-tool.md)  
Raportuje wszystkie zainstalowane wersje środowiska uruchomieniowego języka wspólnego (CLR) na komputerze.

- [Wiersze poleceń](developer-command-prompt-for-vs.md)  
Umożliwia łatwiejsze korzystanie z narzędzi .NET Framework. Jest to wiersz polecenia, który automatycznie ustawia określone zmienne środowiskowe.

- [CorFlags.exe (narzędzie konwersji CorFlags)](corflags-exe-corflags-conversion-tool.md)  
Pozwala skonfigurować sekcję CorFlags w nagłówku obrazu przenośnego pliku wykonywalnego (PE).

- [Fuslogvw.exe (Przeglądarka dzienników powiązań zestawów)](fuslogvw-exe-assembly-binding-log-viewer.md)  
Wyświetla informacji o powiązaniach zestawu pomagające ustalić, dlaczego program .NET Framework nie może zlokalizować zestawu w czasie wykonywania.

- [Gacutil.exe (Global Assembly Cache Tool)](gacutil-exe-gac-tool.md)  
Pozwala wyświetlać i manipulować zawartością globalnej pamięci podręcznej zestawów i pamięci podręcznej pobierania.

- [Ilasm.exe (Asembler IL)](ilasm-exe-il-assembler.md)  
Generuje przenośny plik wykonywalny (PE) z języka pośredniego (IL). Możesz uruchomić wynikowy plik wykonywalny, aby określić, czy IL działa zgodnie z oczekiwaniami.

- [Ildasm.exe (IL dezasembler)](ildasm-exe-il-disassembler.md)  
Pobiera przenośny plik wykonywalny (PE), który zawiera kod języka pośredniego (IL) i tworzy z niego plik tekstowy, który może być użyty jako wejście do asemblera IL (Ilasm.exe).

- [Installutil.exe (narzędzie instalatora)](installutil-exe-installer-tool.md)  
Umożliwia instalowanie i odinstalowywanie zasobów serwera przez wykonywanie składników instalatora w określonym zestawie. (Działa z klasami w <xref:System.Configuration.Install> przestrzeni nazw).

- [Lc.exe (kompilator licencji)](lc-exe-license-compiler.md)  
Odczytuje pliki tekstowe zawierające informacje o licencjonowaniu i tworzy plik *. licenses* , który może być osadzony w pliku wykonywalnym środowiska uruchomieniowego języka wspólnego jako zasób.

- [Mage.exe (Narzędzie tworzenia i edycji manifestów)](mage-exe-manifest-generation-and-editing-tool.md)  
Umożliwia tworzenie, edytowanie i podpisywanie manifestów aplikacji i wdrożenia. Jako narzędzie wiersza polecenia *Mage.exe* można uruchamiać zarówno ze skryptów wsadowych, jak i innych aplikacji opartych na systemie Windows, w tym aplikacji ASP.NET.

- [MageUI.exe (Narzędzie tworzenia i edycji manifestów, klient graficzny)](mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)  
Obsługuje taką samą funkcjonalność jak narzędzie wiersza polecenia Mage.exe, ale używa interfejsu użytkownika (UI) opartego na systemie Windows. Program obsługuje takie same funkcje jak narzędzie wiersza polecenia *Mage.exe*, ale korzysta z interfejsu użytkownika (UI) systemu Windows.

- [MDbg.exe (.NET Framework Debuger wiersza polecenia)](mdbg-exe.md)  
Ułatwia dostawcom narzędzi i deweloperom aplikacji znajdowanie i usuwanie błędów w programach, których platformą docelową jest środowisko uruchomieniowe języka wspólnego programu .NET Framework. To narzędzie używa interfejsu API debugowania środowiska uruchomieniowego w celu dostarczania usług debugowania.

- [Mgmtclassgen.exe (zarządzanie generatorem silnie wpisanej klasy)](mgmtclassgen-exe.md)  
Umożliwia generowanie klasy zarządzanej wcześnie wiązanej dla określonej klasy Instrumentacji zarządzania Windows (WMI, Windows Management Instrumentation).

- [Mpgo.exe (Narzędzie optymalizacji zarządzanego profilu)](mpgo-exe-managed-profile-guided-optimization-tool.md)  
Umożliwia dostrojenie zestawów obrazów natywnych przy użyciu typowych scenariuszy użytkownika końcowego. Mpgo.exe pozwala generować i zużywać dane profilu dla zestawu aplikacji obrazów natywnych (ale nie zestawów .NET Framework) przy użyciu scenariuszy szkoleniowych wybranych przez dewelopera aplikacji.

- [Ngen.exe (Generator obrazu natywnego)](ngen-exe-native-image-generator.md)  
Zwiększa wydajność zarządzanych aplikacji przez użycie obrazów natywnych (plików zawierających skompilowany kod maszynowy specyficzny dla danego procesora). Środowisko uruchomieniowe może używać obrazów natywnych z tej pamięci podręcznej, zamiast używać kompilatora JIT (Just-In-Time) w celu skompilowania oryginalnego zestawu.

- [Peverify.exe (narzędzie PEVerify)](peverify-exe-peverify-tool.md)  
Pomaga w sprawdzaniu, czy kod w języku Microsoft Intermediate Language (MSIL) oraz skojarzone z nim metadane spełniają wymagania dotyczące bezpieczeństwa typów.

- [Regasm.exe (Narzędzie rejestracji zestawów)](regasm-exe-assembly-registration-tool.md)  
Odczytuje metadane w zestawie i dodaje niezbędne wpisy do rejestru. Umożliwia wyświetlane klientów COM jako klas .NET Framework.

- [Regsvcs.exe (Narzędzie instalacji usług .NET)](regsvcs-exe-net-services-installation-tool.md)  
Ładuje i rejestruje zestaw, generuje i instaluje bibliotekę typów w określonej aplikacji COM+ w wersji 1.0 i konfiguruje usługi, które zostały dodane programowo do klasy.

- [Resgen.exe (Generator plików zasobów)](resgen-exe-resource-file-generator.md)  
Konwertuje pliki tekstowe (*. txt* lub *. restext*) i pliki formatu zasobów oparte na formacie XML (*. resx*) na pliki binarne (*. resources*) środowiska uruchomieniowego języka wspólnego, które mogą być osadzone w pliku wykonywalnym binarnym środowiska uruchomieniowego lub skompilowane w zestawach satelickich.

- [SecAnnotate.exe (Narzędzie adnotacji zabezpieczeń .NET)](secannotate-exe-net-security-annotator-tool.md)  
Identyfikuje `SecurityCritical` i `SecuritySafeCritical` fragmenty zestawu.

- [SignTool.exe (Narzędzie podpisywania)](signtool-exe.md)  
Podpisuje cyfrowo pliki, weryfikuje podpisy w plikach oraz oznacza pliki znacznikami czasu.

- [Sn.exe (Narzędzie silnej nazwy)](sn-exe-strong-name-tool.md)  
Pomaga tworzyć zestawy o silnych nazwach. To narzędzie dostarcza opcje do zarządzania kluczami oraz generowania podpisów i weryfikowania ich.

- [SOS.dll (rozszerzenie debugowania SOS)](sos-dll-sos-debugging-extension.md)  
Ułatwia debugowanie programów zarządzanych w debugerze WinDbg.exe i programie Visual Studio, dostarczając informacje na temat wewnętrznego środowiska uruchomieniowego języka wspólnego.

- [SqlMetal.exe (Narzędzie generowania kodu)](sqlmetal-exe-code-generation-tool.md)  
Generuje kod i mapowanie dla składnika LINQ to SQL platformy .NET Framework.

- [Storeadm.exe (Narzędzie izolowanej pamięci masowej)](storeadm-exe-isolated-storage-tool.md)  
Zarządza izolowanym magazynem; dostarcza opcje na potrzeby wyświetlania listy magazynów użytkownika i usuwania ich.

- [Tlbexp.exe (Eksporter biblioteki typów)](tlbexp-exe-type-library-exporter.md)  
Generuje bibliotekę typów opisującą typy, które są zdefiniowane w zestawie środowiska uruchomieniowego języka wspólnego.

- [Tlbimp.exe (Importer biblioteki typów)](tlbimp-exe-type-library-importer.md)  
Konwertuje definicje typów znalezione w bibliotece typów modelu COM do równoważnych definicji w zestawie środowiska uruchomieniowego języka wspólnego.

- [Winmdexp.exe (narzędzie do eksportu metadanych środowisko wykonawcze systemu Windows)](winmdexp-exe-windows-runtime-metadata-export-tool.md)  
Eksportuje zestaw .NET Framework, który jest kompilowany jako plik *. winmdobj* w składniku środowisko wykonawcze systemu Windows, który jest spakowany jako plik *winmd* , który zawiera środowisko wykonawcze systemu Windows metadane i informacje o implementacji.

- [Winres.exe (Windows Forms Edytor zasobów)](winres-exe-windows-forms-resource-editor.md)  
Ułatwia lokalizowanie zasobów interfejsu użytkownika (plików*resx* lub *zasobów* ), które są używane przez Windows Forms. Można tłumaczyć ciągi, a następnie zmieniać rozmiar, przenosić i ukrywać kontrolki, aby pomieścić zlokalizowane ciągi.

## <a name="related-sections"></a>Sekcje pokrewne

- [Narzędzia WPF](https://docs.microsoft.com/previous-versions/ms742404(v=vs.110))  
Obejmuje narzędzia, takie jak narzędzie isXPS zgodności (isXPS.exe) i narzędzia profilowania wydajności.

- [Narzędzia programu Windows Communication Foundation](../wcf/tools.md)  
Zawiera narzędzia, które ułatwiają tworzenie, wdrażanie i zarządzanie aplikacjami Windows Communication Foundation (WCF).
