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
ms.openlocfilehash: b61d079a86bdd4a809d44ad128f19a7b358c8384
ms.sourcegitcommit: b75a45f0cfe012b71b45dd9bf723adf32369d40c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80228677"
---
# <a name="assemblies-in-net"></a>Zestawy w środowisku .NET

Zestawy tworzą podstawowe jednostki wdrażania, kontroli wersji, ponownego użycia, zakresu aktywacji i uprawnień zabezpieczeń dla programu . Aplikacje oparte na sieci. Zestaw jest kolekcją typów i zasobów, które są zbudowane do współpracy i tworzą logiczną jednostkę funkcjonalności. Zestawy mają formę plików wykonywalnych (*.exe*) lub biblioteki łączy dynamicznych (*.dll*) i są budulcem aplikacji .NET. Zapewniają one środowisko uruchomieniowe języka wspólnego z informacjami, które muszą być świadomi implementacji typu.

W .NET Core i .NET Framework można utworzyć zestaw z jednego lub więcej plików kodu źródłowego. W .NET Framework zestawy mogą zawierać jeden lub więcej modułów. Dzięki temu większe projekty mają być planowane tak, że kilku deweloperów może pracować na oddzielnych plików kodu źródłowego lub modułów, które są łączone w celu utworzenia pojedynczego zestawu. Aby uzyskać więcej informacji na temat modułów, zobacz [Jak: Tworzenie zestawu wieloplikowego](../../framework/app-domains/build-multifile-assembly.md).

Zestawy mają następujące właściwości:

- Zestawy są implementowane jako pliki *exe* lub *.dll.*

- W przypadku bibliotek przeznaczonych dla programu .NET Framework można udostępniać zestawy między aplikacjami, umieszczając je w [globalnej pamięci podręcznej zestawów (GAC).](../../framework/app-domains/gac.md) Aby można było dołączyć je do plików GAC, należy dołączyć zestawy o silnej nazwie. Aby uzyskać więcej informacji, zobacz [Zestawy o silnych nazwach](strong-named.md).

- Zestawy są ładowane do pamięci tylko wtedy, gdy są wymagane. Jeśli nie są używane, nie są ładowane. Oznacza to, że zestawy mogą być skutecznym sposobem zarządzania zasobami w większych projektach.

- Można programowo uzyskać informacje o zestawie za pomocą odbicia. Aby uzyskać więcej informacji, zobacz [Odbicie (C#)](../../csharp/programming-guide/concepts/reflection.md) lub [Odbicie (Visual Basic)](../../visual-basic/programming-guide/concepts/reflection.md).

- Można załadować zestaw tylko po to, aby sprawdzić go przy użyciu <xref:System.Reflection.MetadataLoadContext> klasy w .NET Core i <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> lub <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A?displayProperty=nameWithType> metody w .NET Core i .NET Framework.

## <a name="assemblies-in-the-common-language-runtime"></a>Zestawy w czasie wykonywania języka wspólnego

Zestawy zapewniają środowisko uruchomieniowe języka wspólnego z informacjami, które muszą być świadomi implementacji typu. Do środowiska wykonawczego typu nie istnieje poza kontekstem zestawu.

Zestaw definiuje następujące informacje:

- Kod, który wykonuje środowisko uruchomieniowe języka wspólnego. Należy zauważyć, że każdy zestaw `DllMain`może `WinMain`mieć `Main`tylko jeden punkt wejścia: , , lub .

- Granica zabezpieczeń. Zestaw jest jednostką, w której wymagane i udzielone są uprawnienia. Aby uzyskać więcej informacji na temat granic zabezpieczeń w zestawach, zobacz [Zagadnienia dotyczące zabezpieczeń zestawu](security-considerations.md).

- Obwiednia typu. Tożsamość każdego typu zawiera nazwę zestawu, w którym się znajduje. Typ o `MyType` nazwie, który jest ładowany w zakresie jednego `MyType` zestawu nie jest taki sam jak typ, który jest ładowany w zakresie innego zestawu.

- Granica zakresu odwołania. [Manifest zestawu](#assembly-manifest) ma metadane, które są używane do rozpoznawania typów i spełniania żądań zasobów. Manifest określa typy i zasoby do udostępnienia poza zestawem i wylicza inne zestawy, od których zależy. Kod języka pośredniego firmy Microsoft (MSIL) w przenośnym pliku wykonywalnym (PE) nie zostanie wykonany, chyba że ma skojarzony [manifest zestawu](#assembly-manifest).

- Granica wersji. Zestaw jest najmniejszą jednostką konfigurowalną w czasie wykonywania języka wspólnego. Wszystkie typy i zasoby w tym samym zestawie są wersjona jako jednostka. [Manifest zestawu](#assembly-manifest) opisuje zależności wersji, które można określić dla wszystkich zestawów zależnych. Aby uzyskać więcej informacji na temat przechowywania wersji, zobacz [Przechowywanie wersji zestawu](versioning.md).

- Jednostki rozmieszczenia. Po uruchomieniu aplikacji, tylko zestawy, które aplikacja początkowo wywołuje musi być obecny. Inne zestawy, takie jak zestawy zawierające zasoby lokalizacyjne lub klasy narzędzi, można pobrać na żądanie. Dzięki temu aplikacje mogą być proste i cienkie po pierwszym pobraniu. Aby uzyskać więcej informacji na temat wdrażania zestawów, zobacz [Wdrażanie aplikacji](../../framework/deployment/index.md).

- Jednostka wykonawcza obok siebie. Aby uzyskać więcej informacji na temat uruchamiania wielu wersji zestawu, zobacz [Zestawy i wykonanie obok siebie.](side-by-side-execution.md)

## <a name="create-an-assembly"></a>Tworzenie złożenia

Złożenia mogą być statyczne lub dynamiczne. Zestawy statyczne są przechowywane na dysku w przenośnych plikach wykonywalnych (PE). Zestawy statyczne mogą zawierać interfejsy, klasy i zasoby, takie jak mapy bitowe, pliki JPEG i inne pliki zasobów. Można również utworzyć zestawy dynamiczne, które są uruchamiane bezpośrednio z pamięci i nie są zapisywane na dysku przed wykonaniem. Po ich wykonaniu można zapisać zestawy dynamiczne na dysku.

Istnieje kilka sposobów tworzenia zestawów. Można użyć narzędzi programistycznych, takich jak Visual Studio, które można tworzyć pliki *dll* lub *.exe.* Za pomocą narzędzi w zestaw windows SDK można tworzyć zestawy z modułami z innych środowisk programistycznych. Można również użyć interfejsów API środowiska wykonawczego <xref:System.Reflection.Emit?displayProperty=nameWithType>języka wspólnego, takich jak , aby utworzyć zestawy dynamiczne.

Kompiluj zestawy, tworząc je w programie Visual Studio, tworząc je za pomocą narzędzi interfejsu wiersza polecenia .NET Core lub tworząc zestawy .NET Framework za pomocą kompilatora wiersza polecenia. Aby uzyskać więcej informacji na temat tworzenia zestawów przy użyciu interfejsu wiersza polecenia .NET Core, zobacz [omówienie interfejsu wiersza polecenia rdzenia .NET](../../core/tools/index.md). Aby uzyskać informacje o zestawach z kompilatorami wiersza polecenia, zobacz [Kompilacja wiersza polecenia za pomocą pliku csc.exe](../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) dla języka C#lub [Kompilacja z wiersza polecenia](../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) dla języka Visual Basic.

> [!NOTE]
> Aby utworzyć zestaw w programie Visual Studio, w menu **Kompilacja** wybierz polecenie **Buduj**.

## <a name="assembly-manifest"></a>Manifest zestawu

Każdy zestaw ma plik *manifestu zestawu.* Podobnie jak w spisie treści, manifest zestawu zawiera:

- Tożsamość zestawu (jego nazwa i wersja).

- Tabela plików opisująca wszystkie inne pliki tworzące zestaw, takie jak inne zestawy utworzone przez plik *.exe* lub *.dll,* pliki bitmapowe lub pliki Readme.

- *Lista odwołań do zestawu*, która jest listą wszystkich zależności zewnętrznych, takich jak *.dll*s lub inne pliki. Odwołania do zestawu zawierają odwołania do obiektów globalnych i prywatnych. Obiekty globalne są dostępne dla wszystkich innych aplikacji. W .NET Core obiekty globalne są połączone z określonym czasem wykonywania .NET Core. W .NET Framework obiekty globalne znajdują się w globalnej pamięci podręcznej zestawów (GAC). *System.IO.dll* jest przykładem zestawu w gac. Obiekty prywatne muszą znajdować się na poziomie katalogu na poziomie lub poniżej katalogu, w którym jest zainstalowana aplikacja.

Ponieważ zestawy zawierają informacje o zawartości, przechowywanie wersji i zależności, aplikacje, które z nich korzystają, nie muszą polegać na źródłach zewnętrznych, takich jak rejestr w systemach Windows, do poprawnego działania. Zestawy zmniejszają konflikty *dll* i sprawiają, że aplikacje są bardziej niezawodne i łatwiejsze do wdrożenia. W wielu przypadkach można zainstalować program . Aplikacja oparta na sieci po prostu kopiując swoje pliki na komputer docelowy. Aby uzyskać więcej informacji, zobacz [Manifest zestawu](manifest.md).

## <a name="add-a-reference-to-an-assembly"></a>Dodawanie odwołania do zestawu

Aby użyć zestawu w aplikacji, należy dodać do niego odwołanie. Po odwołaniu się do zestawu wszystkie dostępne typy, właściwości, metody i inne elementy członkowskie jego obszarów nazw są dostępne dla aplikacji tak, jakby ich kod był częścią pliku źródłowego.

> [!NOTE]
> Większość zestawów z biblioteki klas .NET odwołuje się automatycznie. Jeśli zestaw systemowy nie jest automatycznie odwoływany, dla .NET Core, można dodać odwołanie do pakietu NuGet, który zawiera zestaw. Użyj Menedżera pakietów NuGet w programie Visual Studio lub dodaj [ \<element packagereference>](../../core/tools/dependencies.md#the-packagereference-element) dla zestawu do projektu *.csproj* lub *.vbproj.* W programie .NET Framework można dodać odwołanie do zestawu za pomocą okna dialogowego `-reference` Dodaj **odwołanie** w programie Visual Studio lub za pomocą opcji wiersza polecenia dla kompilatorów języka [C#](../../csharp/language-reference/compiler-options/reference-compiler-option.md) lub [Visual Basic.](../../visual-basic/reference/command-line-compiler/reference.md)

W języku C# można użyć dwóch wersji tego samego zestawu w jednej aplikacji. Aby uzyskać więcej informacji, zobacz [alias extern](../../csharp/language-reference/keywords/extern-alias.md).

## <a name="related-content"></a>Zawartość pokrewna

|Tytuł|Opis|
|-----------|-----------------|
|[Zawartość zestawu](contents.md)|Elementy, które tworzą zespół.|
|[Manifest złożenia](manifest.md)|Dane w manifeście zestawu i sposób ich przechowywania w złożeniach.|
|[Globalna pamięć podręczna zestawów](../../framework/app-domains/gac.md)|Jak GAC przechowuje i używa zestawów.|
|[Zestawy o silnych nazwach](strong-named.md)|Charakterystyka zespołów o silnych nazwach.|
|[Zagadnienia dotyczące zabezpieczeń zestawów](security-considerations.md)|Jak działa zabezpieczenia z zestawami.|
|[Przechowywanie wersji zestawu](versioning.md)|Omówienie zasad przechowywania wersji programu .NET Framework.|
|[Umieszczanie zestawu](../../framework/app-domains/assembly-placement.md)|Gdzie można zlokalizować złożenia.|
|[Zestawy i wykonywanie równoczesne](side-by-side-execution.md)|Użyj wielu wersji środowiska wykonawczego lub zestawu jednocześnie.|
|[Emitowanie dynamicznych metod i zestawów](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)|Jak utworzyć zestawy dynamiczne.|
|[Jak środowisko wykonawcze lokalizuje zestawy](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)|Jak .NET Framework rozpoznaje odwołania do zestawu w czasie wykonywania.|

## <a name="reference"></a>Tematy pomocy

<xref:System.Reflection.Assembly?displayProperty=nameWithType>

## <a name="see-also"></a>Zobacz też

- [Format pliku zestawu .NET](file-format.md)
- [Przyjazne zestawy](friend.md)
- [Odwoływanie się do zestawów](reference-assemblies.md)
- [Jak: Załaduj i rozładuj zespoły](load-unload.md)
- [Jak: Używanie i debugowanie możliwości rozładunku zestawu w rdzeniu .NET](unloadability.md)
- [Jak: Ustalenie, czy plik jest zestawem](identify.md)
- [Jak: Sprawdzanie zawartości zestawu przy użyciu metadataLoadContext](inspect-contents-using-metadataloadcontext.md)
