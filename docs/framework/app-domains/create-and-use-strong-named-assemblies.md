---
title: Tworzenie i używanie zestawów o silnej nazwie
ms.date: 08/01/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8ee49009915273cc1e16917805f1801268ca0d26
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46009339"
---
# <a name="create-and-use-strong-named-assemblies"></a>Tworzenie i używanie zestawów o silnych nazwach

Silna nazwa składa się z tożsamości zestawu — jego nazwa prosty tekst, numeru wersji i informacji o kulturze (jeśli zostały zapewnione) — plus klucza publicznego i podpisu cyfrowego. Jest generowany na podstawie pliku zestawu przy użyciu odpowiedniego klucza prywatnego. (Plik zestawu zawiera manifest zestawu, który zawiera nazwy i wartości skrótów wszystkich plików, wchodzące w skład zestawu).

> [!WARNING]
> Nie należy polegać na silne nazwy dla zabezpieczeń. Zapewniają one tylko unikatową tożsamość.

Zestaw o silnej nazwie można używać tylko typów od innych zestawów o silnych nazwach. W przeciwnym razie integralności zestawu o silnej nazwie może być narażone na ataki.

## <a name="strong-name-scenario"></a>Scenariusz silnej nazwy

Poniższy scenariusz przedstawia proces podpisywanie zestawu silną nazwą, a później odwoływania się do niego o takiej nazwie.

1.  Zestaw A jest tworzony za pomocą silnej nazwy przy użyciu jednej z następujących metod:

    -   Przy użyciu środowiska programowania, który obsługuje tworzenie silnej nazwy, takie jak Visual Studio.

    -   Tworzenie pary kluczy kryptograficznych za pomocą [narzędzie silnych nazw (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) i przypisywanie tej pary kluczy do zestawu przy użyciu wiersza polecenia kompilatora lub [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md). Zestaw Windows Software Development Kit (SDK) zawiera zarówno Sn.exe, jak i Al.exe.

2.  Środowisko projektowe i narzędzia podpisuje skrót pliku zawierającego manifest zestawu przy użyciu klucza prywatnego dla deweloperów. Podpis cyfrowy jest przechowywany w przenośny plik wykonywalny (PE), który zawiera manifest zestawu A.

3.  Zestaw B jest konsumenta zestawu A. Sekcja odwołanie do manifestu zestawu B zawiera token, który reprezentuje klucz publiczny zestawu A. Token jest częścią klucza publicznego pełnej i jest używana zamiast sam klucz, aby zaoszczędzić miejsce na.

4.  Środowisko uruchomieniowe języka wspólnego weryfikuje podpisu silnej nazwy, gdy zestawu znajduje się w globalnej pamięci podręcznej. Podczas tworzenia powiązania przez silną nazwę w czasie wykonywania, środowisko uruchomieniowe języka wspólnego porównuje klucz przechowywany w manifeście zestawu B przy użyciu klucza, służącego do generowania silnej nazwy zestawu A. Jeśli — dostęp próbny kontrole zabezpieczeń .NET Framework i powiązania zakończy się powodzeniem, Assembly B ma gwarancji, że bity zestawu, A nie został zmodyfikowany i że bity te faktycznie pochodzą od programistów języka zestawu A.

> [!NOTE]
> W tym scenariuszu nie rozwiązać problemy z zaufaniem. Zespoły mogą przenosić pełne podpisy Microsoft Authenticode oprócz silnej nazwy. Sygnatur Authenticode obejmują certyfikat, który ustanawia relację zaufania. Należy zauważyć, że silne nazwy nie wymagają kodu, aby zalogować się w ten sposób. Silne nazwy zapewniają tylko unikatową tożsamość.

## <a name="bypass-signature-verification-of-trusted-assemblies"></a>Weryfikacja podpisu obejścia zaufanych zestawów

Począwszy od [!INCLUDE[net_v35SP1_long](../../../includes/net-v35sp1-long-md.md)], podpisy silnej nazwy nie są weryfikowane, gdy zestaw jest ładowany do domeny, zaufaną aplikację, takie jak domyślnej domeny aplikacji dla `MyComputer` strefy. Jest to określane jako silnej nazwy pomijania funkcji. W pełni zaufanym środowisku, zażąda dla <xref:System.Security.Permissions.StrongNameIdentityPermission> zawsze kończą się pomyślnie dla podpisanej zestawów pełnego zaufania, niezależnie od ich podpisu. Funkcja pomijania silnej nazwy pozwala uniknąć niepotrzebnych nakładów pracy weryfikacji podpisu silnej nazwy zestawów pełnego zaufania w tej sytuacji, dzięki czemu zestawy, które mają ładować się szybciej.

Funkcja pomijania ma zastosowanie do dowolnego złożenia, który jest podpisany silną nazwą i ma następujące cechy:

-   W pełni zaufany, bez <xref:System.Security.Policy.StrongName> dowodów (na przykład `MyComputer` strefa dowód).

-   Ładowany do w pełni zaufany <xref:System.AppDomain>.

-   Ładowane z lokalizacji w obszarze <xref:System.AppDomainSetup.ApplicationBase%2A> właściwość, która <xref:System.AppDomain>.

-   Nie podpisywane z opóźnieniem.

Tę funkcję można wyłączyć dla poszczególnych aplikacji lub komputera. Zobacz [porady: wyłączanie funkcji pomijania silnej nazwy](../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md).

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Instrukcje: tworzenie pary kluczy publiczny-prywatny](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)|W tym artykule opisano sposób tworzenia pary kluczy kryptograficznych dla podpisywania zestawu.|
|[Instrukcje: podpisywanie zestawu silną nazwą](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)|W tym artykule opisano sposób tworzenia zestawu z silną nazwą.|
|[Poprawa silnego nazywania](../../../docs/framework/app-domains/enhanced-strong-naming.md)|Opis ulepszeń silnych nazw w [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].|
|[Instrukcje: odwołanie do zestawu o silnej nazwie](../../../docs/framework/app-domains/how-to-reference-a-strong-named-assembly.md)|W tym artykule opisano, jak odwoływać się do typów lub zasoby znajdujące się zestawu z silną nazwą w czasie kompilacji lub czasu wykonywania.|
|[Instrukcje: wyłączanie funkcji pomijania silnej nazwy](../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md)|Opisuje sposób wyłączania funkcji, które Pomija weryfikację podpisy silnej nazwy. Tę funkcję można wyłączyć dla wszystkich lub określonych aplikacji.|
|[Tworzenie zestawów](../../../docs/framework/app-domains/create-assemblies.md)|Zawiera omówienie pojedynczego pliku i wieloplikowe zestawy.|
|[Sposób opóźnić Podpisz zestaw w programie Visual Studio](/visualstudio/ide/managing-assembly-and-manifest-signing#how-to-sign-an-assembly-in-visual-studio)|Wyjaśnia, jak podpisać zestaw silną nazwą, po utworzeniu zestawu.|
|[Sn.exe (narzędzie silnych nazw)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)|W tym artykule opisano narzędzia zawarte w .NET Framework, która pomaga tworzyć zestawy o silnych nazwach. To narzędzie dostarcza opcje do zarządzania kluczami oraz generowania podpisów i weryfikowania ich.|
|[Al.exe (konsolidator zestawów)](../../../docs/framework/tools/al-exe-assembly-linker.md)|W tym artykule opisano narzędzia zawarte w .NET Framework, która generuje plik z manifestem zestawu z modułów lub zasobów plików.|
