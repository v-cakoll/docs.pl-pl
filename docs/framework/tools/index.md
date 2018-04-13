---
title: Narzędzia programu .NET Framework
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- command line, .NET Framework tools
- .NET Framework, tools
- tools [.NET Framework]
- running .NET Framework tools
ms.assetid: a2ca532d-91f7-426a-9303-417c2ee1247c
caps.latest.revision: 65
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2615c7b8c75f7736bbf8334512790d0a5c43c8d1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="net-framework-tools"></a>Narzędzia programu .NET Framework
Narzędzia programu .NET Framework ułatwiają tworzenie i wdrażanie aplikacji oraz składników współpracujących z programem .NET Framework oraz zarządzanie nimi.  
  
 Większość narzędzi programu .NET Framework, które są opisane w tej sekcji, jest automatycznie instalowana z programem Visual Studio. (Aby uzyskać informacje dotyczące instalacji, zobacz [programu Visual Studio pobiera](http://go.microsoft.com/fwlink/?LinkID=325532).)  
  
 Można uruchomić wszystkie narzędzia z wiersza polecenia, z wyjątkiem Assembly Cache Viewer (Shfusion.dll). Należy przejść do Shfusion.dll z Eksploratora plików.  
  
 Najlepszym sposobem uruchamiania narzędzi wiersza polecenia jest używanie wiersza polecenia dla deweloperów w programie Visual Studio. Te funkcje umożliwiają łatwe uruchamianie narzędzi bez przechodzenia do folderu instalacji. Aby uzyskać więcej informacji, zobacz [wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
> [!NOTE]
>  Niektóre narzędzia są właściwe dla komputerów 32- lub 64-bitowych. Należy pamiętać, aby uruchomić wersję narzędzia odpowiednią dla swojego komputera.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Al.exe (konsolidator zestawów)](../../../docs/framework/tools/al-exe-assembly-linker.md)  
 Generuje plik z manifestem zestawu z modułów lub plików zasobów.  
  
 [Aximp.exe (importer kontrolki ActiveX formularzy Windows Forms)](../../../docs/framework/tools/aximp-exe-windows-forms-activex-control-importer.md)  
 Konwertuje definicje typów w bibliotece typów modelu COM dla formantu ActiveX do formantu Windows Forms.  
  
 [Caspol.exe (narzędzie zasad zabezpieczeń dostępu do kodu)](../../../docs/framework/tools/caspol-exe-code-access-security-policy-tool.md)  
 Umożliwia wyświetlanie i konfigurowanie zasad zabezpieczeń na poziomie zasad komputera, poziomie zasad użytkownika i poziomie zasad przedsiębiorstwa. W [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] i później, to narzędzie nie wpływa na zasady zabezpieczeń (CAS) kodu dostępu chyba że [ \<legacyCasPolicy > element](../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) ma ustawioną wartość `true`. Aby uzyskać więcej informacji, zobacz [zmiany zabezpieczeń](../../../docs/framework/security/security-changes.md).  
  
 [Cert2spc.exe (narzędzie testowe certyfikatów wydawców oprogramowania)](../../../docs/framework/tools/cert2spc-exe-software-publisher-certificate-test-tool.md)  
 Tworzy certyfikat wydawcy oprogramowania (SPC) na podstawie co najmniej jednego certyfikatu X.509. To narzędzie jest przeznaczone wyłącznie do celów testowych.  
  
 [Certmgr.exe (menedżer certyfikatów)](../../../docs/framework/tools/certmgr-exe-certificate-manager-tool.md)  
 Zarządza certyfikatami, listami zaufania certyfikatów (CTL) i listami odwołania certyfikatów (CRL).  
  
 [Clrver.exe (narzędzie wersji środowiska CLR)](../../../docs/framework/tools/clrver-exe-clr-version-tool.md)  
 Raporty wszystkich zainstalowanych wersji środowisko uruchomieniowe języka wspólnego (CLR) na komputerze.  
  
 [CorFlags.exe (narzędzie konwersji CorFlags)](../../../docs/framework/tools/corflags-exe-corflags-conversion-tool.md)  
 Pozwala skonfigurować sekcję CorFlags w nagłówku obrazu przenośnego pliku wykonywalnego (PE).  
  
 [Fuslogvw.exe (podgląd dziennika powiązań zasobów)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md)  
 Wyświetla informacji o powiązaniach zestawu pomagające ustalić, dlaczego program .NET Framework nie może zlokalizować zestawu w czasie wykonywania.  
  
 [Gacutil.exe (narzędzie Global Assembly Cache)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)  
 Pozwala wyświetlać i manipulować zawartością globalnej pamięci podręcznej zestawów i pamięci podręcznej pobierania.  
  
 [Ilasm.exe (asembler IL)](../../../docs/framework/tools/ilasm-exe-il-assembler.md)  
 Generuje przenośny plik wykonywalny (PE) z języka pośredniego (IL). Możesz uruchomić wynikowy plik wykonywalny, aby określić, czy IL działa zgodnie z oczekiwaniami.  
  
 [Ildasm.exe (dezasembler IL)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)  
 Pobiera przenośny plik wykonywalny (PE), który zawiera kod języka pośredniego (IL) i tworzy z niego plik tekstowy, który może być użyty jako wejście do asemblera IL (Ilasm.exe).  
  
 [Installutil.exe (narzędzie instalatora)](../../../docs/framework/tools/installutil-exe-installer-tool.md)  
 Umożliwia instalowanie i odinstalowywanie zasobów serwera przez wykonywanie składników instalatora w określonym zestawie. (Współpracuje z klas w <xref:System.Configuration.Install> przestrzeni nazw.) Umożliwia instalowanie i odinstalowywanie zasobów serwera przez wykonywanie składników instalatora w określonym zestawie. (Współpracuje z klas w <xref:System.Configuration.Install> przestrzeni nazw.)  
  
 [Lc.exe (kompilator licencji)](../../../docs/framework/tools/lc-exe-license-compiler.md)  
 Czyta pliki tekstowe, które zawierają informacje o licencjonowaniu i tworzy plik .licenses, który może zostać osadzony jako zasób w pliku wykonywalnym środowiska uruchomieniowego języka wspólnego. Czyta pliki tekstowe, które zawierają informacje o licencjonowaniu i tworzy plik .licenses, który może zostać osadzony jako zasób w pliku wykonywalnym środowiska uruchomieniowego języka wspólnego.  
  
 [Mage.exe (narzędzie generowania manifestu i edytowania)](../../../docs/framework/tools/mage-exe-manifest-generation-and-editing-tool.md)  
 Umożliwia tworzenie, edytowanie i podpisywanie manifestów aplikacji i wdrożenia. Jako narzędzie wiersza polecenia Mage.exe może być uruchamiane zarówno ze skryptów wsadowych, jak i innych aplikacji opartych na systemie Windows, w tym z aplikacji ASP.NET.  
  
 [MageUI.exe (narzędzie generowania i edytowania manifestu, klient z interfejsem graficznym)](../../../docs/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)  
 Obsługuje taką samą funkcjonalność jak narzędzie wiersza polecenia Mage.exe, ale używa interfejsu użytkownika (UI) opartego na systemie Windows. Obsługuje taką samą funkcjonalność jak narzędzie wiersza polecenia Mage.exe, ale używa interfejsu użytkownika (UI) opartego na systemie Windows.  
  
 [MDbg.exe (debuger wiersza polecenia w programie .NET Framework)](../../../docs/framework/tools/mdbg-exe.md)  
 Ułatwia dostawcom narzędzi i deweloperom aplikacji znajdowanie i usuwanie błędów w programach, których platformą docelową jest środowisko uruchomieniowe języka wspólnego programu .NET Framework. To narzędzie używa interfejsu API debugowania środowiska uruchomieniowego w celu dostarczania usług debugowania.  
  
 [Mgmtclassgen.exe (zarządzanie generatorem silnie typizowanej klasy)](../../../docs/framework/tools/mgmtclassgen-exe.md)  
 Umożliwia generowanie klasy zarządzanej wcześnie wiązanej dla określonej klasy Instrumentacji zarządzania Windows (WMI, Windows Management Instrumentation).  
  
 [Mpgo.exe (narzędzie optymalizacji sterowania zarządzanym profilem)](../../../docs/framework/tools/mpgo-exe-managed-profile-guided-optimization-tool.md)  
 Umożliwia dostrojenie zestawów obrazów natywnych przy użyciu typowych scenariuszy użytkownika końcowego. Mpgo.exe pozwala generować i zużywać dane profilu dla zestawu aplikacji obrazów natywnych (ale nie zestawów .NET Framework) przy użyciu scenariuszy szkoleniowych wybranych przez dewelopera aplikacji.  
  
 [Ngen.exe (generator obrazu natywnego)](../../../docs/framework/tools/ngen-exe-native-image-generator.md)  
 Zwiększa wydajność zarządzanych aplikacji przez użycie obrazów natywnych (plików zawierających skompilowany kod maszynowy specyficzny dla danego procesora). Środowisko uruchomieniowe może używać obrazów natywnych z tej pamięci podręcznej, zamiast używać kompilatora JIT (Just-In-Time) w celu skompilowania oryginalnego zestawu.  
  
 [Peverify.exe (narzędzie PEVerify)](../../../docs/framework/tools/peverify-exe-peverify-tool.md)  
 Pomaga w sprawdzaniu, czy kod w języku Microsoft Intermediate Language (MSIL) oraz skojarzone z nim metadane spełniają wymagania dotyczące bezpieczeństwa typów. Pomaga w sprawdzaniu, czy kod w języku Microsoft Intermediate Language (MSIL) oraz skojarzone z nim metadane spełniają wymagania dotyczące bezpieczeństwa typów.  
  
 [Regasm.exe (narzędzie rejestracji zestawów)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md)  
 Odczytuje metadane w zestawie i dodaje niezbędne wpisy do rejestru. Umożliwia wyświetlane klientów COM jako klas .NET Framework.  
  
 [Regsvcs.exe (narzędzie instalacji usług .NET)](../../../docs/framework/tools/regsvcs-exe-net-services-installation-tool.md)  
 Ładuje i rejestruje zestaw, generuje i instaluje bibliotekę typów w określonej aplikacji COM+ w wersji 1.0 i konfiguruje usługi, które zostały dodane programowo do klasy.  
  
 [Resgen.exe (generator pliku zasobów)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md)  
 Konwertuje pliki tekstowe (.txt lub .restext) i pliki w formacie zasobów opartym na XML (.resx) na pliki danych binarnych środowiska uruchomieniowego języka wspólnego (.resources), które mogą zostać osadzone w wykonywalnym pliku danych binarnych środowiska uruchomieniowego lub skompilowane do zestawów satelickich.  
  
 [SecAnnotate.exe (narzędzie adnotacji dotyczące zabezpieczeń w programach .NET)](../../../docs/framework/tools/secannotate-exe-net-security-annotator-tool.md)  
 Identyfikuje części SecurityCritical i SecuritySafeCritical zestawu. Identyfikuje `SecurityCritical` i `SecuritySafeCritical` części zestawu.  
  
 [SignTool.exe (narzędzie podpisywania)](../../../docs/framework/tools/signtool-exe.md)  
 Podpisuje cyfrowo pliki, weryfikuje podpisy w plikach oraz oznacza pliki znacznikami czasu.  
  
 [Sn.exe (narzędzie silnych nazw)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)  
 Pomaga tworzyć zestawy o silnych nazwach. To narzędzie dostarcza opcje do zarządzania kluczami oraz generowania podpisów i weryfikowania ich.  
  
 [SOS.dll (rozszerzenie do debugowania SOS)](../../../docs/framework/tools/sos-dll-sos-debugging-extension.md)  
 Ułatwia debugowanie programów zarządzanych w debugerze WinDbg.exe i programie Visual Studio, dostarczając informacje na temat wewnętrznego środowiska uruchomieniowego języka wspólnego.  
  
 [SqlMetal.exe (narzędzie generowania kodu)](../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)  
 Generuje kod i mapowanie dla składnika LINQ to SQL platformy .NET Framework.  
  
 [Storeadm.exe (narzędzie wydzielonej pamięci masowej)](../../../docs/framework/tools/storeadm-exe-isolated-storage-tool.md)  
 Zarządza izolowanym magazynem; dostarcza opcje na potrzeby wyświetlania listy magazynów użytkownika i usuwania ich.  
  
 [Tlbexp.exe (eksporter biblioteki typów)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md)  
 Generuje bibliotekę typów opisującą typy, które są zdefiniowane w zestawie środowiska uruchomieniowego języka wspólnego.  
  
 [Tlbimp.exe (importer biblioteki typów)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md)  
 Konwertuje definicje typów znalezione w bibliotece typów modelu COM do równoważnych definicji w zestawie środowiska uruchomieniowego języka wspólnego.  
  
 [Winmdexp.exe (narzędzie eksportowania metadanych środowiska uruchomieniowego systemu Windows)](../../../docs/framework/tools/winmdexp-exe-windows-runtime-metadata-export-tool.md)  
 Eksportuje zestawu .NET Framework, która ma być kompilowana jako plik .winmdobj do składnika środowiska wykonawczego systemu Windows, która jest dostarczana jako plik winmd, który zawiera zarówno informacje metadanych i implementacji środowiska wykonawczego systemu Windows.  
  
 [Winres.exe (Edytor zasobów formularzy Windows Forms)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md)  
 Pomaga lokalizować zasoby (pliki .resx lub .resources) interfejsu użytkownika (UI), które są używane przez Windows Forms. Można tłumaczyć ciągi, a następnie zmieniać rozmiar, przenosić i ukrywać kontrolki, aby pomieścić zlokalizowane ciągi.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Narzędzia](http://msdn.microsoft.com/library/f533241c-317c-445e-88ca-c80c8d078fca)  
 Obejmuje narzędzia, takie jak narzędzie zgodności isXPS (isXPS.exe) i narzędzia profilowania wydajności.  
  
 [Narzędzia programu Windows Communication Foundation](../../../docs/framework/wcf/tools.md)  
 Zawiera narzędzia, które ułatwiają tworzenie, wdrażanie i zarządzanie aplikacjami Windows Communication Foundation (WCF).
