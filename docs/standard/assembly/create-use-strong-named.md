---
title: Tworzenie i używanie silnej nazwy ssemblies
ms.date: 08/19/2019
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
ms.openlocfilehash: 55869c107d245738df3af5ca9bb1b22195e90024
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973321"
---
# <a name="create-and-use-strong-named-assemblies"></a>Tworzenie i używanie zestawów o silnych nazwach

Silna nazwa składa się z tożsamości zestawu — nazwy zwykłego tekstu, numeru wersji i informacji o kulturze (jeśli zostały podane) — oraz klucza publicznego i podpisu cyfrowego. Jest generowany na podstawie pliku zestawu przy użyciu odpowiedniego klucza prywatnego. (Plik zestawu zawiera manifest zestawu, który zawiera nazwy i skróty wszystkich plików, które tworzą zestaw).

> [!WARNING]
> Nie należy polegać na silnych nazwach zabezpieczeń. Zapewniają one tylko unikatową tożsamość.

Zestaw o silnej nazwie może używać tylko typów z innych zestawów o silnych nazwach. W przeciwnym razie integralność zestawu o silnej nazwie zostałaby naruszona.

> [!NOTE]
> Chociaż platforma .NET Core obsługuje zestawy o silnych nazwach, a wszystkie zestawy w bibliotece .NET Core są podpisane, większość zestawów innych firm nie potrzebuje silnych nazw. Aby uzyskać więcej informacji, zobacz [Logowanie silnej nazwy](https://github.com/dotnet/corefx/blob/master/Documentation/project-docs/strong-name-signing.md) w serwisie GitHub.

## <a name="strong-name-scenario"></a>Scenariusz silnej nazwy

W poniższym scenariuszu opisano proces podpisywania zestawu o silnej nazwie i późniejszego odwoływania go przez tę nazwę.

1. Zestaw A jest tworzony za pomocą silnej nazwy przy użyciu jednej z następujących metod:

    - Używanie środowiska programistycznego, które obsługuje tworzenie silnych nazw, takich jak Visual Studio.

    - Tworzenie pary kluczy kryptograficznych za pomocą [Narzędzia silnej nazwy (SN. exe)](../../framework/tools/sn-exe-strong-name-tool.md) i przypisywanie tej pary kluczy do zestawu przy użyciu kompilatora wiersza polecenia lub [konsolidatora zestawu (Al. exe)](../../framework/tools/al-exe-assembly-linker.md). Windows SDK zapewnia zarówno SN. exe, jak i Al. exe.

2. Środowisko programistyczne lub narzędzie podpisuje skrót pliku zawierającego manifest zestawu z kluczem prywatnym dewelopera. Ten podpis cyfrowy jest przechowywany w przenośnym pliku wykonywalnym (PE), który zawiera manifest zestawu A.

3. Zestaw B jest konsumentem zespołu A. Sekcja Reference manifestu zestawu B zawiera token reprezentujący klucz publiczny zestawu A. Token jest częścią pełnego klucza publicznego i jest używany zamiast samego klucza w celu zaoszczędzenia miejsca.

4. Środowisko uruchomieniowe języka wspólnego weryfikuje podpis silnej nazwy, gdy zestaw znajduje się w globalnej pamięci podręcznej zestawów. Podczas tworzenia powiązania przez silną nazwę w czasie wykonywania, środowisko uruchomieniowe języka wspólnego porównuje klucz zapisany w manifeście zestawu B z kluczem użytym do wygenerowania silnej nazwy dla zestawu A. Jeśli .NET Framework sprawdzanie zabezpieczeń zakończy się pomyślnie, zestaw B ma gwarancję, że bity zestawu A nie zostały naruszone i że te bity rzeczywiście pochodzą od deweloperów zestawu A.

> [!NOTE]
> Ten scenariusz nie dotyczy problemów z zaufaniem. Zestawy mogą przenosić pełne podpisy Authenticode firmy Microsoft oprócz silnej nazwy. Podpisy Authenticode zawierają certyfikat, który ustanawia relację zaufania. Należy pamiętać, że silne nazwy nie wymagają podpisania kodu w ten sposób. Silne nazwy zapewniają tylko unikatową tożsamość.

## <a name="bypass-signature-verification-of-trusted-assemblies"></a>Pomijanie weryfikacji sygnatury zaufanych zestawów

Począwszy od .NET Framework 3,5 z dodatkiem Service Pack 1, sygnatury silnej nazwy nie są sprawdzane, gdy zestaw jest ładowany do domeny aplikacji w pełni zaufanej, takiej jak domyślna domena `MyComputer` aplikacji dla strefy. Jest to nazywane funkcją pomijania silnej nazwy. W środowisku pełnego zaufania wymagania dotyczące <xref:System.Security.Permissions.StrongNameIdentityPermission> zawsze powiodło się dla podpisanych, pełnych zestawów, niezależnie od ich sygnatur. Funkcja pomijania silnej nazwy pozwala uniknąć niepotrzebnego narzutu na sygnaturę o silnej nazwie w przypadku zestawów o pełnym zaufaniu w tej sytuacji, co umożliwia szybsze ładowanie zestawów.

Funkcja Bypass ma zastosowanie do każdego zestawu, który jest podpisany silną nazwą i ma następującą charakterystykę:

- W pełni zaufane <xref:System.Security.Policy.StrongName> bez dowodu (na przykład `MyComputer` zawiera dowody strefy).

- Załadowano w pełni zaufany <xref:System.AppDomain>.

- Załadowany z lokalizacji pod <xref:System.AppDomainSetup.ApplicationBase%2A> właściwością. <xref:System.AppDomain>

- Nie jest podpisany z opóźnieniem.

Tę funkcję można wyłączyć dla poszczególnych aplikacji lub dla komputera. Zobacz [How to: Wyłącz funkcję](disable-strong-name-bypass-feature.md)pomijania silnej nazwy.

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Instrukcje: Tworzenie pary kluczy publiczny-prywatny](create-public-private-key-pair.md)|Opisuje sposób tworzenia pary kluczy kryptograficznych do podpisywania zestawu.|
|[Instrukcje: Podpisz zestaw silną nazwą](sign-strong-name.md)|Opisuje sposób tworzenia zestawu o silnej nazwie.|
|[Ulepszone silne nazewnictwo](enhanced-strong-naming.md)|Opisuje ulepszenia dotyczące silnych nazw w .NET Framework 4,5.|
|[Instrukcje: Odwołuje się do zestawu o silnej nazwie](reference-strong-named.md)|Opisuje, jak odwoływać się do typów lub zasobów w zestawie o silnej nazwie w czasie kompilacji lub w czasie wykonywania.|
|[Instrukcje: Wyłącz funkcję pomijania silnej nazwy](disable-strong-name-bypass-feature.md)|Zawiera opis sposobu wyłączania funkcji, która pomija weryfikację sygnatur silnej nazwy. Tę funkcję można wyłączyć dla wszystkich lub dla określonych aplikacji.|
|[Tworzenie zestawów](create.md)|Zawiera omówienie zestawów jednoplikowych i wieloplikowych.|
|[Jak opóźniać podpisywanie zestawu w programie Visual Studio](/visualstudio/ide/managing-assembly-and-manifest-signing#how-to-sign-an-assembly-in-visual-studio)|Wyjaśnia, jak podpisać zestaw silną nazwą po utworzeniu zestawu.|
|[SN. exe (Narzędzie silnej nazwy)](../../framework/tools/sn-exe-strong-name-tool.md)|Zawiera opis narzędzia dołączonego do .NET Framework, które ułatwia tworzenie zestawów o silnych nazwach. To narzędzie dostarcza opcje do zarządzania kluczami oraz generowania podpisów i weryfikowania ich.|
|[Al. exe (Konsolidator zestawu)](../../framework/tools/al-exe-assembly-linker.md)|Opisuje narzędzie zawarte w .NET Framework, które generuje plik z manifestem zestawu z modułów lub plików zasobów.|
