---
title: Zestawy w środowisku .NET
ms.date: 07/10/2018
ms.assetid: 149f5ca5-5b34-4746-9542-1ae43b2d0256
---
# <a name="assemblies-in-net"></a>Zestawy w środowisku .NET

Zespoły tworzą podstawową jednostką wdrażania, kontroli wersji, ponownego użycia, określania zakresu aktywacji i uprawnień zabezpieczeń. Aplikacja oparta na sieci. Zestawy formę dołączana dynamicznie biblioteka (dll) pliku lub plik wykonywalny (.exe) i są blokami konstrukcyjnymi aplikacji .NET. Zapewniają one środowiska uruchomieniowego języka wspólnego informacje, które musi być znane implementacje typu. Można potraktować zestawu jako kolekcję typów i zasobów, które tworzą jednostkę logiczną funkcji i zostały opracowane w celu współpracują ze sobą.  
  
 .NET Core i .NET Framework zestawu może być skompilowana z jednego lub więcej plików kodu źródłowego. W programie .NET Framework zespoły mogą zawierać przynajmniej jeden moduł. Dzięki temu większe projekty zaplanować to działanie w taki sposób, że kilka indywidualnych deweloperów pracować nad plikami kodu źródłowego w oddzielnych lub moduły, które są łączone w celu utworzenia w jednym zestawie. Aby uzyskać więcej informacji na temat modułów, zobacz [jak: Kompilacja zestawów wieloplikowych](../../framework/app-domains/how-to-build-a-multifile-assembly.md).
  
 Zestawy mają następujące właściwości:  
  
-   Zestawy są implementowane jako pliki .exe lub .dll.  
  
-   Dla bibliotek przeznaczonych dla platformy .NET Framework, można udostępniać między aplikacjami przez umieszczenie go w zestawie [globalnej pamięci podręcznej](../../framework/app-domains/gac.md). Zestawy muszą być o silnej nazwie aby mogły zostać uwzględnione w globalnej pamięci podręcznej. Aby uzyskać więcej informacji, zobacz [zestawy Strong-Named](../../framework/app-domains/strong-named-assemblies.md).  
  
-   Zestawy są ładowane do pamięci tylko wtedy, jeśli są one wymagane. Jeśli nie są one używane, nie są one załadowane. Oznacza to, że zestawy może być wydajnym sposobem zarządzania zasobami w dużych projektach.  
  
-   Informacje o zestawie można uzyskać programistycznie przy użyciu odbicia. Aby uzyskać więcej informacji, zobacz [odbicie (C#)](../../csharp/programming-guide/concepts/reflection.md) lub [odbicie (Visual Basic)](../../visual-basic/programming-guide/concepts/reflection.md).   
  
-   Można załadować zestawu, tylko, aby sprawdzić, wywołując metodę <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A?displayProperty=nameWithType>.  
  
## <a name="assembly-manifest"></a>Manifest zestawu  
 W ramach każdego zestawu jest *manifestu zestawu*. Podobnie jak w spisie treści, manifest zestawu zawiera następujące informacje:  
  
-   Tożsamość zestawu (jego nazwa i wersja).  
  
-   Tabeli plików, zawierająca opis wszystkich innych plików, wchodzące w skład zestawu, takich jak inne zespoły utworzonego pliku .exe lub .dll opiera się na, lub nawet mapa bitowa lub pliki Readme.  
  
-   *Listę odwołań zestawu*, który znajduje się lista wszystkich zależności zewnętrznych — dll debuggle lub inne pliki do potrzeb aplikacji, które mogą zostać utworzone przez inną osobę. Odwołania do zestawów zawierają odwołania do obiektów globalnych i prywatnych. Obiekty globalne są dostępne dla wszystkich innych aplikacjach. W .NET Core są powiązane z określonym środowisko uruchomieniowe platformy .NET Core. W programie .NET Framework, zostaną one umieszczone w globalnej pamięci podręcznej. <xref:System.IO?displayProperty=nameWithType> Przestrzeni nazw jest przykładem zestawu w globalnej pamięci podręcznej. Obiekty prywatne musi znajdować się w katalogu na poziomie tym samym poziomie, jak i poniżej katalogu, w którym jest zainstalowana aplikacja.  
  
 Ponieważ zestawy zawierają informacje o zawartości, przechowywanie wersji i zależności, aplikacje, które z nich korzystają, nie należy polegać don Windows wartości rejestru w celu poprawnego. Zestawy zmniejszyć konflikty .dll i dzięki którym Twoje aplikacje bardziej niezawodne i łatwiejsze do wdrożenia. W wielu przypadkach można zainstalować. Aplikacja oparta na sieci poprzez kopiowaniem plików do komputera docelowego. Aby uzyskać więcej informacji, zobacz [manifestu zestawu](../../framework/app-domains/assembly-manifest.md).  
  
## <a name="adding-a-reference-to-an-assembly"></a>Dodawanie odwołania do zestawu  
 Aby korzystać z zestawu, należy dodać odwołanie do niej. Następnie możesz użyć [użycie dyrektywy](../../csharp/language-reference/keywords/using-directive.md) dla C# lub [Imports — instrukcja](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) dla języka Visual Basic wybrać przestrzeń nazw elementów, w której chcesz użyć. Gdy odwołanie do zestawu i zaimportowaniu dostępnych typów, właściwości, metod i inni członkowie jej przestrzenie nazw są dostępne dla aplikacji tak, jakby ich kod były częścią pliku źródłowego.  
 
> [!NOTE]
> Większość zestawów z biblioteki klas .NET odwołuje się automatycznie. W niektórych przypadkach jednak zestaw systemowy może nie automatycznie odwoływać. W .NET Core, można dodać odwołania do pakietu NuGet, który zawiera zestaw przy użyciu Menedżera pakietów NuGet w programie Visual Studio lub dodając [ <PackageReference> ](../../core/tools/dependencies.md#the-new-packagereference-element) element zestawu w projekcie *.csproj lub *.vbproj. W programie .NET Framework, można dodać odwołanie do zestawu przy użyciu **Dodaj odwołanie** okna dialogowego w programie Visual Studio lub za pomocą `-reference` opcji wiersza polecenia dla [ C# ](../../csharp/language-reference/compiler-options/reference-compiler-option.md) lub [ Visual Basic](../../visual-basic/reference/command-line-compiler/reference.md) kompilatory.
 
 W języku C# umożliwia także dwie wersje tego samego zestawu w jednej aplikacji. Aby uzyskać więcej informacji, zobacz [alias zewnętrzny](../../csharp/language-reference/keywords/extern-alias.md).  
  
## <a name="creating-an-assembly"></a>Tworzenie zestawu  
 Skompiluj aplikację, tworząc go w programie Visual Studio, tworząc z wiersza polecenia przy użyciu narzędzi interfejsu wiersza polecenia (CLI) platformy .NET Core lub tworząc zestawów .NET Framework za pomocą kompilatora wiersza polecenia. Aby uzyskać więcej informacji o tworzeniu zestawów przy użyciu narzędzi interfejsu wiersza polecenia platformy .NET, zobacz [narzędzi interfejsu wiersza polecenia (CLI) platformy .NET Core](../../core/tools/index.md). Do tworzenia zestawów za pomocą kompilatorów wiersza polecenia, zobacz [kompilacji wiersza polecenia przy użyciu csc.exe](../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) dla C# i [tworzenie z wiersza polecenia](../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) dla języka Visual Basic.  
  
> [!NOTE]
>  Tworzenie zestawu w programie Visual Studio na **kompilacji** menu wybierz opcję **kompilacji**.  

## <a name="see-also"></a>Zobacz także

 - [Format pliku zestawu .NET](file-format.md)
 - [Zestawy w środowisku uruchomieniowym CLR](../../framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 - [Przyjazne zestawy](friend-assemblies.md)  
 - [Instrukcje: Ładowanie i zwalnianie zestawów (C#)](../../csharp/programming-guide/concepts/assemblies-gac/how-to-load-and-unload-assemblies.md)  
 - [Instrukcje: Ładowanie i zwalnianie zestawów (Visual Basic)](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-load-and-unload-assemblies.md)  
 - [Instrukcje: Użycie i debugowanie funkcji zwolnienia zestawu w programie .NET Core](unloadability-howto.md)
 - [Instrukcje: Określić, czy plik jest zestawem (C#)](../../csharp/programming-guide/concepts/assemblies-gac/how-to-determine-if-a-file-is-an-assembly.md)  
 - [Instrukcje: Określić, czy plik jest zestawem (Visual Basic)](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-determine-if-a-file-is-an-assembly.md)  
