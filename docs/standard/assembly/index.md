---
title: Zestawy w środowisku .NET
ms.date: 07/10/2018
ms.assetid: 149f5ca5-5b34-4746-9542-1ae43b2d0256
ms.openlocfilehash: 09dc44141a4eea7601df3f918e8740efdb99aeda
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666592"
---
# <a name="assemblies-in-net"></a>Zestawy w środowisku .NET

Zestawy stanowią podstawową jednostkę wdrożenia, kontrolę wersji, ponowne użycie, zakres aktywacji i uprawnienia zabezpieczeń dla. Aplikacja oparta na sieci. Zestawy przyjmują postać pliku wykonywalnego (exe) lub pliku biblioteki dołączanej dynamicznie (. dll) i są blokami konstrukcyjnymi aplikacji .NET. Udostępniają one środowisko uruchomieniowe języka wspólnego z informacjami, które muszą być świadome implementacji typów. Zestaw można traktować jako kolekcję typów i zasobów, które tworzą logiczną jednostkę funkcjonalności i są zbudowane do współdziałania ze sobą.

W programie .NET Core i .NET Framework Zestaw można skompilować z jednego lub większej liczby plików kodu źródłowego. W .NET Framework zestawy mogą zawierać co najmniej jeden moduł. Pozwala to na planowanie większych projektów w taki sposób, że kilku indywidualnych deweloperów pracuje nad oddzielnymi plikami kodu źródłowego lub modułami, które są łączone w celu utworzenia jednego zestawu. Aby uzyskać więcej informacji o modułach [, zobacz How to: Kompiluj zestaw](../../framework/app-domains/how-to-build-a-multifile-assembly.md)wieloplikowy.

Zestawy mają następujące właściwości:

- Zestawy są zaimplementowane jako pliki exe lub dll.

- W przypadku bibliotek przeznaczonych dla .NET Framework można udostępnić zestaw między aplikacjami, umieszczając je w [globalnej pamięci podręcznej zestawów](../../framework/app-domains/gac.md). Zestawy muszą mieć silne nazwy, aby można je było uwzględnić w globalnej pamięci podręcznej zestawów. Aby uzyskać więcej informacji, zobacz [zestawy o silnych nazwach](../../framework/app-domains/strong-named-assemblies.md).

- Zestawy są ładowane do pamięci tylko wtedy, gdy są wymagane. Jeśli nie są używane, nie są ładowane. Oznacza to, że zestawy mogą być wydajnym sposobem zarządzania zasobami w większych projektach.

- Można programowo uzyskać informacje o zestawie przy użyciu odbicia. Aby uzyskać więcej informacji, zobacz [odbicieC#()](../../csharp/programming-guide/concepts/reflection.md) lub odbicie [(Visual Basic)](../../visual-basic/programming-guide/concepts/reflection.md).

- Zestaw można załadować tylko do inspekcji przy użyciu <xref:System.Reflection.MetadataLoadContext> klasy.

## <a name="assembly-manifest"></a>Manifest zestawu

W każdym zestawie jest *manifestem zestawu*. Podobnie jak w spisie treści, manifest zestawu zawiera następujące elementy:

- Tożsamość zestawu (jego nazwa i wersja).

- Tabela plików opisująca wszystkie inne pliki wchodzące w skład zestawu, na przykład inne zestawy, które zostały utworzone przez plik. exe lub. dll, lub nawet pliki map bitowych lub Readme.

- *Lista odwołania do zestawu*, która jest listą wszystkich zależności zewnętrznych — bibliotek DLL lub innych plików potrzebnych przez aplikację, które mogły zostać utworzone przez kogoś innego. Odwołania do zestawów zawierają odwołania do obiektów globalnych i prywatnych. Obiekty globalne są dostępne dla wszystkich innych aplikacji. W programie .NET Core są one połączone z konkretnym środowiskiem uruchomieniowym platformy .NET Core. W .NET Framework znajdują się one w globalnej pamięci podręcznej zestawów. <xref:System.IO?displayProperty=nameWithType> Przestrzeń nazw jest przykładem zestawu w globalnej pamięci podręcznej zestawów. Obiekty prywatne muszą znajdować się w katalogu na tym samym poziomie co lub w katalogu, w którym zainstalowano aplikację.

Ponieważ zestawy zawierają informacje o zawartości, wersji i zależnościach, aplikacje, które ich używają, nie muszą polegać na wartościach rejestru systemu Windows w celu poprawnego działania. Zestawy zmniejszają konflikty biblioteki DLL i sprawiają, że aplikacje są bardziej niezawodne i łatwiejsze do wdrożenia. W wielu przypadkach można zainstalować program. Aplikacje oparte na sieci można po prostu skopiować pliki na komputer docelowy. Aby uzyskać więcej informacji, zobacz [manifest zestawu](../../framework/app-domains/assembly-manifest.md).

## <a name="adding-a-reference-to-an-assembly"></a>Dodawanie odwołania do zestawu

Aby użyć zestawu, należy dodać odwołanie do niego. Następnie można użyć [dyrektywy using](../../csharp/language-reference/keywords/using-directive.md) dla C# lub [Imports instrukcji](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) dla Visual Basic, aby wybrać przestrzeń nazw elementów, które mają być używane. Po przywoływaniu i zaimportowaniu zestawu wszystkie dostępne typy, właściwości, metody i inne elementy członkowskie jego przestrzeni nazw są dostępne dla aplikacji, tak jakby ich kod był częścią pliku źródłowego.

> [!NOTE]
> Większość zestawów z biblioteki klas .NET jest przywoływana automatycznie. W niektórych przypadkach, chociaż zestaw systemowy może nie być automatycznie przywoływany. W oprogramowaniu .NET Core można dodać odwołanie do pakietu NuGet zawierającego zestaw przy użyciu Menedżera pakietów NuGet w programie Visual Studio lub przez dodanie [ \<elementu PackageReference >](../../core/tools/dependencies.md#the-new-packagereference-element) dla zestawu do projektu *. csproj lub *. vbproj. W .NET Framework można dodać odwołanie do zestawu przy użyciu okna dialogowego **Dodawanie odwołania** w programie Visual Studio lub przy użyciu `-reference` opcji wiersza polecenia dla kompilatorów [C#](../../csharp/language-reference/compiler-options/reference-compiler-option.md) lub [Visual Basic](../../visual-basic/reference/command-line-compiler/reference.md) .

W C#programie można również użyć dwóch wersji tego samego zestawu w pojedynczej aplikacji. Aby uzyskać więcej informacji, zobacz [alias zewnętrzny](../../csharp/language-reference/keywords/extern-alias.md).

## <a name="creating-an-assembly"></a>Tworzenie zestawu

Kompiluj swoją aplikację przez skompilowanie jej w programie Visual Studio, tworząc ją z wiersza polecenia przy użyciu narzędzi interfejsu wiersza polecenia (CLI) platformy .NET Core lub tworząc zestawy .NET Framework przy użyciu kompilatora wiersza polecenia. Aby uzyskać więcej informacji na temat kompilowania zestawów przy użyciu narzędzi [interfejsu wiersza polecenia platformy .NET, zobacz narzędzia platformy .NET Core Command Interface (CLI)](../../core/tools/index.md). Do kompilowania zestawów przy użyciu kompilatorów wiersza polecenia, zobacz [wiersza polecenia Build z usługą CSC. exe](../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) dla C# i [Kompilowanie z wiersza polecenia](../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) dla Visual Basic.

> [!NOTE]
> Aby skompilować zestaw w programie Visual Studio, w menu **kompilacja** wybierz polecenie **Kompiluj**.

## <a name="see-also"></a>Zobacz także

- [Format pliku zestawu .NET](file-format.md)
- [Zestawy w środowisku uruchomieniowym CLR](../../framework/app-domains/assemblies-in-the-common-language-runtime.md)
- [Przyjazne zestawy](friend-assemblies.md)
- [Instrukcje: Ładowanie i zwalnianie zestawówC#()](../../csharp/programming-guide/concepts/assemblies-gac/how-to-load-and-unload-assemblies.md)
- [Instrukcje: Ładowanie i zwalnianie zestawów (Visual Basic)](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-load-and-unload-assemblies.md)
- [Instrukcje: Użycie i debugowanie funkcji zwolnienia zestawu w programie .NET Core](unloadability-howto.md)
- [Instrukcje: Ustal, czy plik jest zestawem (C#)](../../csharp/programming-guide/concepts/assemblies-gac/how-to-determine-if-a-file-is-an-assembly.md)
- [Instrukcje: Ustal, czy plik jest zestawem (Visual Basic)](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-determine-if-a-file-is-an-assembly.md)
