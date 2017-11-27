---
title: "Tworzenie i używanie zestawów o silnej nazwie"
ms.date: 08/01/2017
ms.prod: .net-framework
ms.technology: dotnet-bcl
ms.topic: article
helpviewer_keywords:
- strong-name bypass feature
- strong-named assemblies, about strong-named assemblies
- strong-named assemblies
- signing assemblies
- assemblies [.NET Framework], signing
- strong-named assemblies, scenarios
- assemblies [.NET Framework], strong-named
- strong-named assemblies, loading into trusted application domains
- assembly binding, strong-named
ms.assetid: ffbf6d9e-4a88-4a8a-9645-4ce0ee1ee5f9
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 39fbd38549a791a761c633dca90dbdeeeefce10b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="creating-and-using-strong-named-assemblies"></a>Tworzenie i używanie zestawów o silnej nazwie
<a name="top"></a>Silnej nazwy składa się z tożsamości zestawu — zwykły tekst nazwa, numer wersji i informacje o ustawieniach kulturowych (jeśli jest dostępny) — oraz klucz publiczny i podpis cyfrowy. Jest generowany na podstawie pliku zestawu przy użyciu odpowiedniego klucza prywatnego. (Plik zestawu zawiera manifest zestawu, który zawiera nazwy i wartości skrótu wszystkie pliki wchodzące w skład zestawu).  
  
 Zestaw o silnej nazwie można używać tylko typów od innych zestawów o silnych nazwach. W przeciwnym razie integralność zestawu o silnej nazwie może zostać naruszone.  
  
 Ten przegląd zawiera następujące sekcje:  
  
-   [Scenariusz silnej nazwy](#strong_name_scenario)  
  
-   [Pomijanie weryfikacji podpisu zaufanych zestawów](#bypassing_signature_verification)  
  
-   [Tematy pokrewne](#related_topics)  
  
<a name="strong_name_scenario"></a>   
## <a name="strong-name-scenario"></a>Scenariusz silnej nazwy  
 Poniższy scenariusz przedstawiono proces podpisywania zestawu o silnej nazwie i później odwołania do o takiej nazwie.  
  
1.  Zestaw A jest tworzony przy użyciu silnej nazwy przy użyciu jednej z następujących metod:  
  
    -   Używanie środowiska projektowania, który obsługuje tworzenie silne nazwy, takie jak [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)].  
  
    -   Tworzenie za pomocą klucza kryptograficznego [narzędzie Strong Name (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) i przypisywanie tej pary kluczy do zestawu przy użyciu wiersza polecenia kompilatora lub [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md). Zestaw Windows Software Development Kit (SDK), udostępnia Sn.exe oraz Al.exe.  
  
2.  Środowisko projektowe lub narzędzia podpisuje skrótu pliku zawierającego manifest zestawu z kluczem prywatnym dewelopera. Podpis cyfrowy jest przechowywany w przenośnym pliku wykonywalnego pliku (PE), który zawiera manifest zestawu A.  
  
3.  Zestaw B jest konsumenta zestawu A. Ta część manifestu zestawu B zawiera token, który reprezentuje klucz publiczny zestawu A. Token jest częścią klucza publicznego pełnej i jest używany zamiast samego klucza, aby zaoszczędzić miejsce.  
  
4.  Środowisko uruchomieniowe języka wspólnego weryfikuje podpisu silnej nazwy, gdy zestaw jest umieszczony w pamięci podręcznej GAC. Podczas tworzenia wiązania przy użyciu silnej nazwy w czasie wykonywania, środowisko uruchomieniowe języka wspólnego porównuje klucz przechowywany w manifeście zestawu B przy użyciu klucza używanego do generowania silnej nazwy zestawu A. Jeśli przebieg sprawdzania zabezpieczeń .NET Framework i powiązania zakończy się powodzeniem, B zestawu ma gwarancji, że bitów zestawu, A nie został zmodyfikowany i że te usługi bits faktycznie pochodzą z deweloperzy zestawu A.  
  
> [!NOTE]
>  W tym scenariuszu nie Rozwiąż problemy z zaufania. Zestawy można wykonać pełne podpisy Microsoft Authenticode oprócz silnej nazwy. Sygnatur Authenticode obejmują certyfikat, który ustanawia relację zaufania. Należy pamiętać, że silnych nazw nie wymagają kodu podpisywanego w ten sposób. Silne nazwy zapewniają tylko unikatową tożsamość.  
  
 [Powrót do początku](#top)  
  
<a name="bypassing_signature_verification"></a>   
## <a name="bypassing-signature-verification-of-trusted-assemblies"></a>Pomijanie weryfikacji podpisu zaufanych zestawów  
 Począwszy od [!INCLUDE[net_v35SP1_long](../../../includes/net-v35sp1-long-md.md)], podpisy silnej nazwy nie są weryfikowane, gdy zestaw jest ładowany do domeny aplikacji pełnego zaufania, na przykład domyślnej domeny aplikacji dla `MyComputer` strefy. Jest to określane jako silnej nazwy pomijania funkcji. W pełni zaufanym środowisku, wymaga dla <xref:System.Security.Permissions.StrongNameIdentityPermission> zawsze powiodła się dla podpisanej zestawy pełnego zaufania, niezależnie od ich podpisu. Funkcja pomijania silnej nazwy pozwala uniknąć niepotrzebnych obciążenie weryfikacji podpisu silnej nazwy zestawów pełnego zaufania w tej sytuacji, umożliwiając zestawy załadować szybciej.  
  
 Funkcja pomijania ma zastosowanie do dowolnego zestawu, który jest podpisany przy użyciu silnej nazwy i ma następujące cechy:  
  
-   Pełni zaufany bez <xref:System.Security.Policy.StrongName> dowód (na przykład `MyComputer` strefy dowód).  
  
-   Załadowane w pełni zaufany <xref:System.AppDomain>.  
  
-   Załadowane z lokalizacji w <xref:System.AppDomainSetup.ApplicationBase%2A> właściwości tego <xref:System.AppDomain>.  
  
-   Nie podpisywany z opóźnieniem.  
  
 Tę funkcję można wyłączyć dla poszczególnych aplikacji lub komputera. Zobacz [porady: wyłączanie funkcji pomijania silnej nazwy](../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md).  
  
 [Powrót do początku](#top)  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Porady: tworzenie pary kluczy publiczno prywatnych](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)|Opisuje sposób tworzenia klucza kryptograficznego podpisywania zestawu.|  
|[Porady: podpisać zestaw o silnej nazwie](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)|Opisuje sposób tworzenia zestawu z silną nazwą.|  
|[Poprawa silnego nazywania](../../../docs/framework/app-domains/enhanced-strong-naming.md)|Opisuje rozszerzenia silnych nazw w [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].|  
|[Porady: odwołanie do zestawu o silnej nazwie](../../../docs/framework/app-domains/how-to-reference-a-strong-named-assembly.md)|Opisuje sposób odwoływać się do typów lub zasoby zestawu z silną nazwą w czasie kompilacji lub czasu wykonywania.|  
|[Porady: wyłączanie funkcji pomijania silnej nazwy](../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md)|Opisuje sposób wyłączenia funkcji omija Weryfikacja podpisów silnej nazwy. Tę funkcję można wyłączyć dla wszystkich lub określonych aplikacji.|  
|[Tworzenie zestawów](../../../docs/framework/app-domains/create-assemblies.md)|Zawiera omówienie zestawy jednoplikowe i wiele plików.|  
|[Jak opóźnienie Podpisz zestaw w programie Visual Studio](/visualstudio/ide/managing-assembly-and-manifest-signing#how-to-sign-an-assembly-in-visual-studio)|Wyjaśniono, jak podpisać zestaw o silnej nazwie po utworzeniu zestawu.|  
|[SN.exe (narzędzie silnych nazw)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)|W tym artykule opisano narzędzia uwzględnione w programie .NET Framework, która pomaga utworzyć zestawy o silnych nazwach. To narzędzie dostarcza opcje do zarządzania kluczami oraz generowania podpisów i weryfikowania ich.|  
|[Al.exe (konsolidator zestawów)](../../../docs/framework/tools/al-exe-assembly-linker.md)|W tym artykule opisano narzędzia uwzględnione w programie .NET Framework, który generuje plik manifestu z zasobu lub moduły pliki zestawu.|
