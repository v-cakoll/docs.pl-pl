---
title: Zestawy w środowisku .NET
description: Zestawy to podstawowe jednostki wdrażania, kontroli wersji, ponownego użycia, zakresu aktywacji i uprawnień zabezpieczeń dla programu. Aplikacje oparte na sieci.
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
ms.openlocfilehash: 87030bf9770c464709559b2fb8f4c0004009e48d
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379911"
---
# <a name="assemblies-in-net"></a>Zestawy w środowisku .NET

Zestawy stanowią podstawowe jednostki wdrożenia, kontroli wersji, ponownego użycia, zakresu aktywacji i uprawnień zabezpieczeń dla programu. Aplikacje oparte na sieci. Zestaw jest kolekcją typów i zasobów, które są tworzone w celu współdziałania i tworzą logiczną jednostkę funkcjonalności. Zestawy mają postać plików wykonywalnych (*exe*) lub bibliotek dołączanych dynamicznie (*. dll*) i są blokami konstrukcyjnymi aplikacji .NET. Udostępniają one środowisko uruchomieniowe języka wspólnego z informacjami, które muszą być świadome implementacji typów.

W programie .NET Core i .NET Framework można skompilować zestaw z jednego lub większej liczby plików kodu źródłowego. W .NET Framework zestawy mogą zawierać co najmniej jeden moduł. Pozwala to na zaplanowanie większych projektów w taki sposób, aby kilku deweloperów mógł działać na oddzielnych plikach kodu źródłowego lub w modułach, które są łączone w celu utworzenia jednego zestawu. Aby uzyskać więcej informacji o modułach, zobacz [How to: Build a wieloplikowego zestawu](../../framework/app-domains/build-multifile-assembly.md).

Zestawy mają następujące właściwości:

- Zestawy są zaimplementowane jako pliki *exe* lub *dll* .

- W przypadku bibliotek przeznaczonych dla .NET Framework można udostępniać zestawy między aplikacjami, umieszczając je w [globalnej pamięci podręcznej zestawów (GAC)](../../framework/app-domains/gac.md). Aby można było dołączać je do pamięci podręcznej GAC, należy najpierw zastosować zestawy o silnych nazwach. Aby uzyskać więcej informacji, zobacz [zestawy o silnych nazwach](strong-named.md).

- Zestawy są ładowane do pamięci tylko wtedy, gdy są wymagane. Jeśli nie są używane, nie są ładowane. Oznacza to, że zestawy mogą być wydajnym sposobem zarządzania zasobami w większych projektach.

- Można programowo uzyskać informacje o zestawie przy użyciu odbicia. Aby uzyskać więcej informacji, zobacz [odbicie (C#)](../../csharp/programming-guide/concepts/reflection.md) lub [odbicie (Visual Basic)](../../visual-basic/programming-guide/concepts/reflection.md).

- Możesz załadować zestaw, aby sprawdzić go przy użyciu <xref:System.Reflection.MetadataLoadContext> klasy w .NET Core oraz <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A?displayProperty=nameWithType> metod lub w programie .net core i .NET Framework.

## <a name="assemblies-in-the-common-language-runtime"></a>Zestawy w środowisku uruchomieniowym języka wspólnego

Zestawy zapewniają środowisko uruchomieniowe języka wspólnego z informacjami, które muszą być świadome implementacji typów. Dla środowiska uruchomieniowego typ nie istnieje poza kontekstem zestawu.

Zestaw definiuje następujące informacje:

- Kod wykonywany przez środowisko uruchomieniowe języka wspólnego. Należy zauważyć, że każdy zestaw może mieć tylko jeden punkt wejścia: `DllMain` , `WinMain` , lub `Main` .

- Granica zabezpieczeń. Zestaw jest jednostką, w której uprawnienia są żądane i udzielane. Aby uzyskać więcej informacji na temat granic zabezpieczeń w zestawach, zobacz [zagadnienia dotyczące zabezpieczeń zestawów](security-considerations.md).

- Granica typu. Każda tożsamość typu zawiera nazwę zestawu, w którym znajduje się. Typ o nazwie `MyType` , który jest ładowany w zakresie jednego zestawu, nie jest taki sam jak typ o nazwie `MyType` , który jest ładowany w zakresie innego zestawu.

- Granica zakresu odwołania. [Manifest zestawu](#assembly-manifest) zawiera metadane, który jest używany do rozpoznawania typów i spełniania żądań zasobów. Manifest określa typy i zasoby, które mają zostać ujawnione poza zestawem, i wylicza inne zestawy, na których zależą. Kod języka pośredniego (MSIL) firmy Microsoft w przenośnym pliku wykonywalnym (PE) nie zostanie wykonany, chyba że ma skojarzony [manifest zestawu](#assembly-manifest).

- Granica wersji. Zestaw jest najmniejszą wersją jednostki w środowisku uruchomieniowym języka wspólnego. Wszystkie typy i zasoby w tym samym zestawie są w wersji jako jednostka. [Manifest zestawu](#assembly-manifest) zawiera opis zależności wersji określonych dla wszystkich zestawów zależnych. Aby uzyskać więcej informacji na temat przechowywania wersji, zobacz [wersja zestawu](versioning.md).

- Jednostka wdrożenia. Po uruchomieniu aplikacji, tylko zestawy, które początkowo wywołuje aplikacja, muszą być obecne. Inne zestawy, takie jak zestawy zawierające zasoby lokalizacyjne lub klasy narzędzi, można pobrać na żądanie. Dzięki temu aplikacje będą proste i cienkie podczas pierwszego pobierania. Aby uzyskać więcej informacji o wdrażaniu zestawów, zobacz [wdrażanie aplikacji](../../framework/deployment/index.md).

- Jednostka wykonywania równoczesnego. Aby uzyskać więcej informacji na temat uruchamiania wielu wersji zestawu, zobacz [zestawy i wykonywanie równoczesne](side-by-side-execution.md).

## <a name="create-an-assembly"></a>Tworzenie zestawu

Zestawy mogą być statyczne lub dynamiczne. Zestawy statyczne są przechowywane na dysku w przenośnych plikach wykonywalnych (PE). Zestawy statyczne mogą zawierać interfejsy, klasy i zasoby, takie jak mapy bitowe, pliki JPEG i inne pliki zasobów. Można również tworzyć zestawy dynamiczne, które są uruchamiane bezpośrednio z pamięci i nie są zapisywane na dysku przed wykonaniem. Zestawy dynamiczne można zapisać na dysku po ich wykonaniu.

Istnieje kilka sposobów tworzenia zestawów. Możesz użyć narzędzi programistycznych, takich jak Visual Studio, które mogą tworzyć pliki *. dll* lub *. exe* . Korzystając z narzędzi dostępnych w Windows SDK, można tworzyć zestawy z modułami z innych środowisk programistycznych. Możesz również używać interfejsów API środowiska uruchomieniowego języka wspólnego, takich jak <xref:System.Reflection.Emit?displayProperty=nameWithType> , do tworzenia zestawów dynamicznych.

Kompiluj zestawy, tworząc je w programie Visual Studio, tworząc je przy użyciu narzędzi interfejsu wiersza polecenia platformy .NET Core lub tworząc zestawy .NET Framework przy użyciu kompilatora wiersza polecenia. Aby uzyskać więcej informacji na temat kompilowania zestawów przy użyciu interfejs wiersza polecenia platformy .NET Core, zobacz [interfejs wiersza polecenia platformy .NET Core Omówienie](../../core/tools/index.md). Do kompilowania zestawów przy użyciu kompilatorów wiersza polecenia, zobacz [wiersz polecenia kompilacja za pomocą pliku CSC. exe](../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) dla języka C# lub [Kompiluj z wiersza polecenia](../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) dla Visual Basic.

> [!NOTE]
> Aby skompilować zestaw w programie Visual Studio, w menu **kompilacja** wybierz polecenie **Kompiluj**.

## <a name="assembly-manifest"></a>Manifest zestawu

Każdy zestaw ma plik *manifestu zestawu* . Podobnie jak w spisie treści, manifest zestawu zawiera:

- Tożsamość zestawu (jego nazwa i wersja).

- Tabela plików opisująca wszystkie inne pliki wchodzące w skład zestawu, takie jak inne utworzone zestawy, których plik *exe* lub *dll* opiera się na plikach map bitowych lub plikach Readme.

- *Lista odwołania do zestawu*, która jest listą wszystkich zależności zewnętrznych, takich jak *. dll*s lub innych plików. Odwołania do zestawów zawierają odwołania do obiektów globalnych i prywatnych. Obiekty globalne są dostępne dla wszystkich innych aplikacji. W programie .NET Core obiekty globalne są połączone z konkretnym środowiskiem uruchomieniowym platformy .NET Core. W .NET Framework obiekty globalne znajdują się w globalnej pamięci podręcznej zestawów (GAC). Przykładem zestawu w globalnej pamięci podręcznej jest *System. IO. dll* . Obiekty prywatne muszą znajdować się na poziomie katalogu w katalogu, w którym zainstalowano aplikację.

Ponieważ zestawy zawierają informacje o zawartości, wersji i zależnościach, aplikacje korzystające z nich nie musi korzystają ze źródeł zewnętrznych, takich jak rejestr w systemach Windows, aby działać prawidłowo. Zestawy zmniejszają konflikty *biblioteki DLL* i sprawiają, że aplikacje są bardziej niezawodne i łatwiejsze do wdrożenia. W wielu przypadkach można zainstalować program. Aplikacje oparte na sieci można po prostu skopiować pliki na komputer docelowy. Aby uzyskać więcej informacji, zobacz [manifest zestawu](manifest.md).

## <a name="add-a-reference-to-an-assembly"></a>Dodawanie odwołania do zestawu

Aby użyć zestawu w aplikacji, należy dodać do niego odwołanie. Po przywoływaniu zestawu wszystkie dostępne typy, właściwości, metody i inne elementy członkowskie jego przestrzeni nazw są dostępne dla aplikacji, tak jakby ich kod był częścią pliku źródłowego.

> [!NOTE]
> Większość zestawów z biblioteki klas .NET jest przywoływana automatycznie. Jeśli zestaw systemowy nie jest automatycznie przywoływany, w przypadku platformy .NET Core można dodać odwołanie do pakietu NuGet, który zawiera zestaw. Użyj Menedżera pakietów NuGet w programie Visual Studio lub Dodaj element [ \< PackageReference>](../../core/tools/dependencies.md#the-packagereference-element) dla zestawu do projektu *. csproj* lub *. vbproj* . W .NET Framework można dodać odwołanie do zestawu przy użyciu okna dialogowego **Dodaj odwołanie** w programie Visual Studio lub przy użyciu `-reference` opcji wiersza polecenia dla kompilatorów [języka C#](../../csharp/language-reference/compiler-options/reference-compiler-option.md) lub [Visual Basic](../../visual-basic/reference/command-line-compiler/reference.md) .

W języku C# można użyć dwóch wersji tego samego zestawu w pojedynczej aplikacji. Aby uzyskać więcej informacji, zobacz [alias zewnętrzny](../../csharp/language-reference/keywords/extern-alias.md).

## <a name="related-content"></a>Zawartość pokrewna

|Tytuł|Opis|
|-----------|-----------------|
|[Zawartość zestawu](contents.md)|Elementy wchodzące w skład zestawu.|
|[Manifest zestawu](manifest.md)|Dane w manifeście zestawu i sposób ich przechowywania w zestawach.|
|[Globalna pamięć podręczna zestawów](../../framework/app-domains/gac.md)|Sposób przechowywania i używania zestawów GAC.|
|[Zestawy o silnych nazwach](strong-named.md)|Charakterystyki zestawów o silnych nazwach.|
|[Zagadnienia dotyczące zabezpieczeń zestawów](security-considerations.md)|Sposób działania zabezpieczeń z zestawami.|
|[Przechowywanie wersji zestawu](versioning.md)|Omówienie zasad dotyczących wersji .NET Framework.|
|[Umieszczanie zestawu](../../framework/app-domains/assembly-placement.md)|Gdzie można znaleźć zestawy.|
|[Zestawy i wykonywanie równoczesne](side-by-side-execution.md)|Używaj jednocześnie wielu wersji środowiska uruchomieniowego lub zestawu.|
|[Emitowanie dynamicznych metod i zestawów](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)|Tworzenie zestawów dynamicznych.|
|[Jak środowisko uruchomieniowe lokalizuje zestawy](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)|Jak .NET Framework rozwiązuje odwołania do zestawów w czasie wykonywania.|

## <a name="reference"></a>Dokumentacja

<xref:System.Reflection.Assembly?displayProperty=nameWithType>

## <a name="see-also"></a>Zobacz też

- [Format pliku zestawu .NET](file-format.md)
- [Przyjazne zestawy](friend.md)
- [Odwoływanie się do zestawów](reference-assemblies.md)
- [Instrukcje: ładowanie i zwalnianie zestawów](load-unload.md)
- [Instrukcje: używanie i debugowanie zestawu do odciążania w programie .NET Core](unloadability.md)
- [Instrukcje: ustalanie, czy plik jest zestawem](identify.md)
- [Instrukcje: inspekcja zawartości zestawu przy użyciu MetadataLoadContext](inspect-contents-using-metadataloadcontext.md)
