---
title: Zestawy w środowisku .NET
ms.date: 08/15/2019
ms.assetid: 149f5ca5-5b34-4746-9542-1ae43b2d0256
helpviewer_keywords:
- dynamic assemblies
- security [.NET Framework], boundaries
- boundaries of assemblies
- assemblies [.NET Framework], about
- assemblies [.NET Framework], boundaries
- reference scope boundaries
- assemblies [.NET Framework]
- version boundaries
- type boundaries
ms.openlocfilehash: f85fef37ac952c91ac73570f26d80d8a46f4eedf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78156508"
---
# <a name="assemblies-in-net"></a>Zestawy w środowisku .NET

Zestawy tworzą podstawowe jednostki wdrażania, kontroli wersji, ponownego użycia, zakresu aktywacji i uprawnień zabezpieczeń dla . aplikacji opartych na sieci. Zestaw jest kolekcją typów i zasobów, które są zbudowane do współpracy i tworzą logiczną jednostkę funkcjonalności. Zestawy mają formę plików wykonywalnych (*exe*) lub biblioteki łączy dynamicznych (*dll*) i są elementami konstrukcyjnymi aplikacji .NET. Zapewniają one czas wykonywania języka wspólnego z informacji potrzebnych do zapoznania się z implementacji typu.

W .NET Core i .NET Framework można utworzyć zestaw z jednego lub więcej plików kodu źródłowego. W programie .NET Framework zestawy mogą zawierać jeden lub więcej modułów. Dzięki temu większe projekty mają być planowane tak, że kilku deweloperów może pracować na oddzielnych plików kodu źródłowego lub modułów, które są łączone w celu utworzenia pojedynczego zestawu. Aby uzyskać więcej informacji na temat modułów, zobacz [Jak: Tworzenie zestawu wieloplikowego](../../framework/app-domains/build-multifile-assembly.md).

Zestawy mają następujące właściwości:

- Zestawy są implementowane jako pliki *exe* lub *dll.*

- W przypadku bibliotek docelowych programu .NET Framework można udostępniać zestawy między aplikacjami, umieszczając je w [globalnej pamięci podręcznej zestawów (GAC).](../../framework/app-domains/gac.md) Należy zestawów o silnej nazwie, zanim będzie można je uwzględnić w gac. Aby uzyskać więcej informacji, zobacz [Zestawy o silnej nazwie](strong-named.md).

- Zestawy są ładowane do pamięci tylko wtedy, gdy są one wymagane. Jeśli nie są używane, nie są ładowane. Oznacza to, że zestawy mogą być efektywnym sposobem zarządzania zasobami w większych projektach.

- Można programowo uzyskać informacje o zestawie za pomocą odbicia. Aby uzyskać więcej informacji, zobacz [Odbicie (C#)](../../csharp/programming-guide/concepts/reflection.md) lub [Odbicie (Visual Basic).](../../visual-basic/programming-guide/concepts/reflection.md)

- Można załadować zestaw tylko do sprawdzenia <xref:System.Reflection.MetadataLoadContext> go przy użyciu <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> klasy <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A?displayProperty=nameWithType> w .NET Core i lub metod w .NET Core i .NET Framework.

## <a name="assemblies-in-the-common-language-runtime"></a>Zestawy w czasie wykonywania języka wspólnego

Zestawy zapewniają czas wykonywania języka wspólnego z informacjami, które należy pamiętać o implementacjach typu. Do czasu wykonywania typu nie istnieje poza kontekstem zestawu.

Zestaw definiuje następujące informacje:

- Kod, który wykonuje program runtime języka wspólnego. Należy zauważyć, że każdy zespół `DllMain`może `WinMain`mieć `Main`tylko jeden punkt wejścia: , , lub .

- Granica zabezpieczeń. Zestaw jest jednostką, w której żąda neamu i przyznawane są uprawnienia. Aby uzyskać więcej informacji o granicach zabezpieczeń w złożeniach, zobacz [Zagadnienia dotyczące zabezpieczeń zestawu](security-considerations.md).

- Granica typu. Tożsamość każdego typu zawiera nazwę zestawu, w którym się znajduje. Typ o `MyType` nazwie, który jest ładowany w zakresie jednego `MyType` zestawu nie jest taki sam jak typ o nazwie, który jest ładowany w zakresie innego zestawu.

- Granica zakresu odwołania. [Manifest zestawu](#assembly-manifest) ma metadane, które są używane do rozpoznawania typów i spełniania żądań zasobów. Manifest określa typy i zasoby, aby udostępnić poza zestawem i wylicza inne zestawy, od których zależy. Kod języka pośredniego firmy Microsoft (MSIL) w przenośnym pliku wykonywalnym (PE) nie zostanie wykonany, chyba że ma skojarzony [manifest zestawu.](#assembly-manifest)

- Granica wersji. Zestaw jest najmniejszą jednostką z możliwością wersji w czasie wykonywania języka wspólnego. Wszystkie typy i zasoby w tym samym zestawie są wersjonowane jako jednostka. [Manifest zestawu](#assembly-manifest) opisuje zależności wersji określone dla wszystkich zestawów zależnych. Aby uzyskać więcej informacji na temat wersji, zobacz [Przechowywanie wersji zestawu](versioning.md).

- Jednostka wdrożeniowa. Po uruchomieniu aplikacji muszą być obecne tylko zestawy, które początkowo wywołuje aplikacja. Inne zestawy, takie jak zestawy zawierające zasoby lokalizacji lub klasy narzędzi, mogą być pobierane na żądanie. Dzięki temu aplikacje mogą być proste i cienkie podczas pierwszego pobrania. Aby uzyskać więcej informacji na temat wdrażania zestawów, zobacz [Wdrażanie aplikacji](../../framework/deployment/index.md).

- Jednostka wykonania obok siebie. Aby uzyskać więcej informacji na temat uruchamiania wielu wersji zestawu, zobacz [Zestawy i wykonanie obok siebie](side-by-side-execution.md).

## <a name="create-an-assembly"></a>Tworzenie złożenia

Złożenia mogą być statyczne lub dynamiczne. Zespoły statyczne są przechowywane na dysku w przenośnych plikach wykonywalnych (PE). Zestawy statyczne mogą zawierać interfejsy, klasy i zasoby, takie jak mapy bitowe, pliki JPEG i inne pliki zasobów. Można również tworzyć zestawy dynamiczne, które są uruchamiane bezpośrednio z pamięci i nie są zapisywane na dysku przed wykonaniem. Można zapisać zestawy dynamiczne na dysku po ich wykonaniu.

Istnieje kilka sposobów tworzenia zestawów. Za pomocą narzędzi programistycznych, takich jak Visual Studio, które mogą tworzyć pliki *dll* lub *.exe.* Za pomocą narzędzi w sdk systemu Windows można tworzyć zestawy z modułami z innych środowisk programistycznych. Można również użyć interfejsów API wykonywania języka wspólnego, takich jak <xref:System.Reflection.Emit?displayProperty=nameWithType>, aby utworzyć zestawy dynamiczne.

Skompiluj zestawy, budując je w programie Visual Studio, budując je za pomocą narzędzi interfejsu wiersza polecenia .NET Core lub tworząc zestawy .NET Framework za pomocą kompilatora wiersza polecenia. Aby uzyskać więcej informacji na temat tworzenia zestawów przy użyciu.NET Core CLI, zobacz [omówienie.NET Core CLI](../../core/tools/index.md). Aby uzyskać informacje na temat tworzenia zestawów za pomocą kompilatorów wiersza polecenia, zobacz [Kompilacja wiersza polecenia z csc.exe](../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) dla języka C#lub [Kompilacja z wiersza polecenia](../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) dla języka Visual Basic.

> [!NOTE]
> Aby utworzyć zestaw w programie Visual Studio, w menu **Kompilacja** wybierz polecenie **Kompilacja**.

## <a name="assembly-manifest"></a>Manifest zestawu

Każdy zestaw ma plik *manifestu zestawu.* Podobnie jak spis treści, manifest zestawu zawiera:

- Tożsamość zestawu (jego nazwa i wersja).

- Tabela plików opisująca wszystkie inne pliki tworzące zestaw, takie jak inne utworzone zestawy, na których opiera się plik *.exe* lub *dll,* pliki bitmaplub pliki Readme.

- *Lista odwołań do zestawu*, która jest listą wszystkich zależności zewnętrznych, takich jak *.dll*s lub inne pliki. Odwołania do zestawu zawierają odwołania do obiektów globalnych i prywatnych. Obiekty globalne są dostępne dla wszystkich innych aplikacji. W .NET Core obiekty globalne są połączone z określonym.NET Core runtime. W ramach programu .NET Framework obiekty globalne znajdują się w globalnej pamięci podręcznej zestawów (GAC). *System.IO.dll* jest przykładem złożenia w gac. Obiekty prywatne muszą znajdować się na poziomie katalogu na poziomie katalogu lub poniżej katalogu, w którym aplikacja jest zainstalowana.

Ponieważ zestawy zawierają informacje o zawartości, przechowywania wersji i zależności, aplikacje, które ich używają, nie muszą polegać na źródłach zewnętrznych, takich jak rejestr w systemach Windows, aby działać poprawnie. Zestawy zmniejszają konflikty *dll* i sprawiają, że aplikacje są bardziej niezawodne i łatwiejsze do wdrożenia. W wielu przypadkach można zainstalować plik . Aplikacja oparta na SIECI po prostu kopiując swoje pliki na komputer docelowy. Aby uzyskać więcej informacji, zobacz [Manifest zestawu](manifest.md).

## <a name="add-a-reference-to-an-assembly"></a>Dodawanie odwołania do złożenia

Aby użyć zestawu w aplikacji, należy dodać odwołanie do niego. Po odwołaniu się do zestawu wszystkie dostępne typy, właściwości, metody i inne elementy członkowskie jego przestrzeni nazw są dostępne dla aplikacji, tak jakby ich kod był częścią pliku źródłowego.

> [!NOTE]
> Większość zestawów z biblioteki klas .NET odwołuje się automatycznie. Jeśli zestaw systemu nie odwołuje się automatycznie, dla .NET Core, można dodać odwołanie do pakietu NuGet, który zawiera zestaw. Użyj Menedżera pakietów NuGet w programie Visual Studio lub dodaj element [ \<PackageReference>](../../core/tools/dependencies.md#the-packagereference-element) dla zestawu do projektu *.csproj* lub *.vbproj.* W programie .NET Framework można dodać odwołanie do zestawu za pomocą okna dialogowego `-reference` Dodawanie **odwołania** w programie Visual Studio lub za pomocą opcji wiersza polecenia dla kompilatorów Języka [C#](../../csharp/language-reference/compiler-options/reference-compiler-option.md) lub [Visual Basic.](../../visual-basic/reference/command-line-compiler/reference.md)

W języku C#, można użyć dwóch wersji tego samego zestawu w jednej aplikacji. Aby uzyskać więcej informacji, zobacz [alias extern](../../csharp/language-reference/keywords/extern-alias.md).

## <a name="related-content"></a>Zawartość pokrewna

|Tytuł|Opis|
|-----------|-----------------|
|[Zawartość zestawu](contents.md)|Elementy, które tworzą zespół.|
|[Manifest montażowy](manifest.md)|Dane w manifeście zestawu i jak są przechowywane w zestawach.|
|[Globalna pamięć podręczna zestawów](../../framework/app-domains/gac.md)|Jak GAC przechowuje i używa zestawów.|
|[Zestawy o silnych nazwach](strong-named.md)|Charakterystyka zespołów o silnej nazwie.|
|[Zagadnienia dotyczące zabezpieczeń zestawów](security-considerations.md)|Jak działa bezpieczeństwo z zespołami.|
|[Przechowywanie wersji zestawu](versioning.md)|Omówienie zasad wersji .NET Framework.|
|[Umieszczanie zestawu](../../framework/app-domains/assembly-placement.md)|Gdzie zlokalizować zespoły.|
|[Zestawy i wykonywanie równoczesne](side-by-side-execution.md)|Należy używać wielu wersji czasu wykonywania lub zestawu jednocześnie.|
|[Emitowanie dynamicznych metod i zestawów](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)|Jak tworzyć zestawy dynamiczne.|
|[Jak program runtime lokalizuje zestawy](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)|Jak program .NET Framework rozwiązuje odwołania do zestawu w czasie wykonywania.|

## <a name="reference"></a>Dokumentacja

<xref:System.Reflection.Assembly?displayProperty=nameWithType>

## <a name="see-also"></a>Zobacz też

- [Format pliku zestawu .NET](file-format.md)
- [Przyjazne zestawy](friend.md)
- [Odwoływanie się do zestawów](reference-assemblies.md)
- [Jak: Załadować i rozładować zespoły](load-unload.md)
- [Instrukcje: Używanie i debugowanie zwalnialności zestawu w .NET Core](unloadability.md)
- [Jak: Określić, czy plik jest złożeniem](identify.md)
