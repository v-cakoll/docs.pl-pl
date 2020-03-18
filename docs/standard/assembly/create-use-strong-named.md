---
title: Tworzenie i używanie zestawów o silnej nazwie
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
ms.openlocfilehash: 18a0b7d657290835a34c705513d0d7a4ccbfc61c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75738685"
---
# <a name="create-and-use-strong-named-assemblies"></a>Tworzenie i używanie zestawów o silnej nazwie

Silna nazwa składa się z tożsamości zestawu — jego prostej nazwy tekstowej, numeru wersji i informacji o kulturze (jeśli zostały dostarczone) oraz klucza publicznego i podpisu cyfrowego. Jest on generowany z pliku zestawu przy użyciu odpowiedniego klucza prywatnego. (Plik zestawu zawiera manifest zestawu, który zawiera nazwy i haszysze wszystkich plików, które tworzą zestaw.)

> [!WARNING]
> Nie należy polegać na silne nazwy dla bezpieczeństwa. Zapewniają one tylko unikatową tożsamość.

Zestaw o silnej nazwie może używać tylko typów z innych zestawów o silnej nazwie. W przeciwnym razie integralność zestawu o silnej nazwie zostanie naruszona.

> [!NOTE]
> Mimo że program .NET Core obsługuje zestawy o silnych nazwach, a wszystkie zestawy w bibliotece .NET Core są podpisane, większość zestawów innych firm nie wymaga silnych nazw. Aby uzyskać więcej informacji, zobacz [Silne podpisywanie nazw](https://github.com/dotnet/runtime/blob/master/docs/project/strong-name-signing.md) w usyjanie usługi GitHub.

## <a name="strong-name-scenario"></a>Scenariusz silnej nazwy

Poniższy scenariusz przedstawia proces podpisywania zestawu o silnej nazwie, a następnie odwoływania się do niego o tej nazwie.

1. Zestaw A jest tworzony z silną nazwą przy użyciu jednej z następujących metod:

    - Przy użyciu środowiska programistycznego, który obsługuje tworzenie silnych nazw, takich jak Visual Studio.

    - Tworzenie pary kluczy kryptograficznych przy użyciu [narzędzia Silna nazwa (Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md) i przypisywanie tej pary kluczy do zestawu przy użyciu kompilatora wiersza polecenia lub [konsolidatora zestawu (Al.exe)](../../framework/tools/al-exe-assembly-linker.md). Zestaw Windows SDK zapewnia zarówno program Sn.exe, jak i program Al.exe.

2. Środowisko programistyczne lub narzędzie podpisuje skrót pliku zawierający manifest zestawu kluczem prywatnym dewelopera. Ten podpis cyfrowy jest przechowywany w przenośnym pliku wykonywalnym (PE), który zawiera manifest zestawu A.

3. Zespół B jest konsumentem zespołu A. Sekcja referencyjna manifestu zestawu B zawiera token, który reprezentuje klucz publiczny zestawu A. Token jest częścią pełnego klucza publicznego i jest używany, a nie sam klucz, aby zaoszczędzić miejsce.

4. Czas wykonywania języka wspólnego weryfikuje podpis silnej nazwy, gdy zestaw jest umieszczony w globalnej pamięci podręcznej zestawów. Podczas wiązania przez silną nazwę w czasie wykonywania, czas wykonywania języka wspólnego porównuje klucz przechowywany w manifeście zestawu B z kluczem używanym do generowania silnej nazwy dla zestawu A. Jeśli sprawdza zabezpieczeń .NET Framework przekazać i powiązanie powiedzie się, zestaw B ma gwarancję, że zestaw a bity nie zostały naruszone i że te bity faktycznie pochodzą od twórców zestawu A.

> [!NOTE]
> W tym scenariuszu nie rozwiązuje problemów z zaufaniem. Zestawy mogą przenosić pełne podpisy Microsoft Authenticode oprócz silnej nazwy. Podpisy uwierzytelnione zawierają certyfikat ustanawiający zaufanie. Należy pamiętać, że silne nazwy nie wymagają kodu do podpisania w ten sposób. Silne nazwy zapewniają tylko unikatową tożsamość.

## <a name="bypass-signature-verification-of-trusted-assemblies"></a>Pomijanie weryfikacji podpisu zaufanych zestawów

Począwszy od .NET Framework 3.5 z dodatkiem Service Pack 1, podpisy o silnej nazwie nie są weryfikowane po `MyComputer` załadowaniu zestawu do domeny aplikacji pełnego zaufania, takiej jak domyślna domena aplikacji dla strefy. Jest to określane jako funkcja pomijania silnej nazwy. W środowisku pełnego zaufania wymagania <xref:System.Security.Permissions.StrongNameIdentityPermission> dotyczące zawsze odnoszą sukcesy w przypadku podpisanych zestawów o pełnym zaufaniu, niezależnie od ich podpisu. Funkcja pomijania silnej nazwy pozwala uniknąć niepotrzebnego obciążenia weryfikacją podpisu o silnej nazwie zestawów pełnego zaufania w tej sytuacji, umożliwiając zespołom szybsze ładowanie.

Funkcja pomijania ma zastosowanie do każdego zestawu, który jest podpisany o silnej nazwie i który ma następujące cechy:

- W pełni <xref:System.Security.Policy.StrongName> zaufany bez dowodów (na przykład ma `MyComputer` dowody strefy).

- Załadowany do <xref:System.AppDomain>w pełni zaufanego .

- Załadowany z lokalizacji <xref:System.AppDomainSetup.ApplicationBase%2A> pod <xref:System.AppDomain>własnością tego .

- Nie zopóźnieniem.

Tę funkcję można wyłączyć w przypadku poszczególnych aplikacji lub komputera. Zobacz [jak: Wyłączyć funkcję pomijania silnej nazwy](disable-strong-name-bypass-feature.md).

## <a name="related-topics"></a>Powiązane tematy

|Tytuł|Opis|
|-----------|-----------------|
|[Jak: Tworzenie pary kluczy publiczno-prywatnych](create-public-private-key-pair.md)|W tym artykule opisano sposób tworzenia pary kluczy kryptograficznych do podpisywania zestawu.|
|[Jak: Podpisywanie zestawu o silnej nazwie](sign-strong-name.md)|Opisuje sposób tworzenia zestawu o silnej nazwie.|
|[Ulepszone silne nazewnictwo](enhanced-strong-naming.md)|W tym artykule opisano ulepszenia silnych nazw w .NET Framework 4.5.|
|[Jak: Odwoływać się do zestawu o silnej nazwie](reference-strong-named.md)|Opisuje sposób odwoływania się do typów lub zasobów w zestawie o silnej nazwie w czasie kompilacji lub w czasie wykonywania.|
|[Jak: Wyłącz funkcję pomijania silnej nazwy](disable-strong-name-bypass-feature.md)|Opisuje sposób wyłączania funkcji, która pomija sprawdzanie poprawności podpisów o silnej nazwie. Tę funkcję można wyłączyć dla wszystkich lub dla określonych aplikacji.|
|[Tworzenie zestawów](create.md)|Zawiera omówienie zestawów jednoplikowych i wieloplikowych.|
|[Jak opóźnić podpisanie zestawu w programie Visual Studio](/visualstudio/ide/managing-assembly-and-manifest-signing#how-to-sign-an-assembly-in-visual-studio)|W tym artykule wyjaśniono, jak podpisać zestaw o silnej nazwie po utworzeniu zestawu.|
|[Sn.exe (narzędzie Silna nazwa)](../../framework/tools/sn-exe-strong-name-tool.md)|Opisuje narzędzie zawarte w platformie .NET Framework, które pomaga tworzyć zestawy o silnych nazwach. To narzędzie dostarcza opcje do zarządzania kluczami oraz generowania podpisów i weryfikowania ich.|
|[Al.exe (konsolidator montażowy)](../../framework/tools/al-exe-assembly-linker.md)|Opisuje narzędzie zawarte w programie .NET Framework, które generuje plik zawierający manifest zestawu z modułów lub plików zasobów.|
