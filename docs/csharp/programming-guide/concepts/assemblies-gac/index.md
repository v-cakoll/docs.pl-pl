---
title: Zestawy i Globalna pamięć podręczna zestawów (C#)
ms.date: 07/20/2015
ms.assetid: 149f5ca5-5b34-4746-9542-1ae43b2d0256
ms.openlocfilehash: ed5ecff57035b4d3cf47f8325fe5c172180f9d40
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43778389"
---
# <a name="assemblies-and-the-global-assembly-cache-c"></a>Zestawy i Globalna pamięć podręczna zestawów (C#)
Zespoły tworzą podstawową jednostką wdrażania, kontroli wersji, ponownego użycia, określania zakresu aktywacji i uprawnień zabezpieczeń. Aplikacja oparta na sieci. Zestawy formę dołączana dynamicznie biblioteka (dll) pliku lub plik wykonywalny (.exe) i są blokami konstrukcyjnymi programu .NET Framework. Zapewniają one środowiska uruchomieniowego języka wspólnego informacje, które musi być znane implementacje typu. Można potraktować zestawu jako kolekcję typów i zasobów, które tworzą jednostkę logiczną funkcji i zostały opracowane w celu współpracują ze sobą.  
  
 Zespoły mogą zawierać przynajmniej jeden moduł. Na przykład większe projekty mogą być planowane w taki sposób, że kilka indywidualnych deweloperów działać na osobne moduły, wszystkie nadchodzące ze sobą, aby utworzyć pojedynczy zestaw. Aby uzyskać więcej informacji na temat modułów, zobacz temat [porady: kompilacja zestawów Multifile](../../../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md).  
  
 Zestawy mają następujące właściwości:  
  
-   Zestawy są implementowane jako pliki .exe lub .dll.  
  
-   Można udostępniać między aplikacjami przez umieszczenie go w globalnej pamięci podręcznej zestawu. Zestawy muszą być o silnej nazwie aby mogły zostać uwzględnione w globalnej pamięci podręcznej. Aby uzyskać więcej informacji, zobacz [zestawy Strong-Named](../../../../../docs/framework/app-domains/strong-named-assemblies.md).  
  
-   Zestawy są ładowane do pamięci tylko wtedy, jeśli są one wymagane. Jeśli nie są one używane, nie są one załadowane. Oznacza to, że zestawy może być wydajnym sposobem zarządzania zasobami w dużych projektach.  
  
-   Informacje o zestawie można uzyskać programistycznie przy użyciu odbicia. Aby uzyskać więcej informacji, zobacz [odbicia (C#)](../../../../csharp/programming-guide/concepts/reflection.md).  
  
-   Jeśli do załadowania zestawu tylko, aby sprawdzić, należy użyć metody takie jak <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A>.  
  
## <a name="assembly-manifest"></a>Manifest zestawu  
 W ramach każdego zestawu istnieje *manifestu zestawu*. Podobnie jak w spisie treści, manifest zestawu zawiera następujące informacje:  
  
-   Tożsamość zestawu (jego nazwa i wersja).  
  
-   Tabela plików opisujące wszystkie pliki wchodzące w skład zestawu, na przykład innych zestawów utworzonych, plik .exe lub .dll opiera się na, lub nawet mapy bitowej i pliki Readme.  
  
-   *Listę odwołań zestawu*, który znajduje się lista wszystkich zależności zewnętrznych — dll debuggle lub inne pliki do potrzeb aplikacji, które mogą zostać utworzone przez inną osobę. Odwołania do zestawów zawierają odwołania do obiektów globalnych i prywatnych. Obiekty globalne znajdują się w globalnej pamięci podręcznej, obszaru, które są dostępne dla innych aplikacji. Obiekty prywatne musi znajdować się w katalogu na poziomie tym samym poziomie, jak i poniżej katalogu, w którym jest zainstalowana aplikacja.  
  
 Ponieważ zestawy zawierają informacje o zawartości, przechowywanie wersji i zależności, aplikacje utworzone przy użyciu języka C# nie należy polegać na wartości rejestru Windows, aby działać prawidłowo. Zestawy zmniejszyć konflikty .dll i dzięki którym Twoje aplikacje bardziej niezawodne i łatwiejsze do wdrożenia. W wielu przypadkach można zainstalować. Aplikacja oparta na sieci poprzez kopiowaniem plików do komputera docelowego.  
  
 Aby uzyskać więcej informacji, zobacz [manifestu zestawu](../../../../../docs/framework/app-domains/assembly-manifest.md).  
  
## <a name="adding-a-reference-to-an-assembly"></a>Dodawanie odwołania do zestawu  
 Aby korzystać z zestawu, należy dodać odwołanie do niej. Następnie użyj [użycie dyrektywy](../../../../csharp/language-reference/keywords/using-directive.md) wybrać przestrzeń nazw elementów, w której chcesz użyć. Gdy odwołanie do zestawu i zaimportowaniu wszystkich dostępnych klas, właściwości, metod i inni członkowie jej przestrzenie nazw są dostępne dla aplikacji tak, jakby ich kod były częścią pliku źródłowego.  
  
 W języku C# umożliwia także dwie wersje tego samego zestawu w jednej aplikacji. Aby uzyskać więcej informacji, zobacz [alias zewnętrzny](../../../../csharp/language-reference/keywords/extern-alias.md).  
  
## <a name="creating-an-assembly"></a>Tworzenie zestawu  
 Kompiluj aplikację, klikając **kompilacji** na **kompilacji** menu lub tworząc je z poziomu wiersza polecenia za pomocą kompilatora wiersza polecenia. Aby uzyskać szczegółowe informacje o tworzeniu zestawów z wiersza polecenia, zobacz [wiersza polecenia tworzenia przy użyciu csc.exe](../../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).  
  
> [!NOTE]
>  Tworzenie zestawu w programie Visual Studio na **kompilacji** menu wybierz opcję **kompilacji**.  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../../../../csharp/programming-guide/index.md)  
- [Zestawy w środowisku uruchomieniowym CLR](../../../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
- [Przyjazne zestawy (C#)](friend-assemblies.md)  
- [Porady: dzielenie się zestawem z innymi aplikacjami (C#)](how-to-share-an-assembly-with-other-applications.md)  
- [Porady: ładowanie i zwalnianie zestawów (C#)](how-to-load-and-unload-assemblies.md)  
- [Porady: Określanie, jeśli plik jest zestawem (C#)](how-to-determine-if-a-file-is-an-assembly.md)  
- [Porady: tworzenie i używanie zestawów przy użyciu wiersza polecenia (C#)](how-to-create-and-use-assemblies-using-the-command-line.md)  
- [Przewodnik: Osadzanie typów z zarządzanych zestawów w programie Visual Studio (C#)](walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)  
- [Przewodnik: Osadzanie informacji o typie z zestawów Microsoft Office w programie Visual Studio (C#)](walkthrough-embedding-type-information-from-microsoft-office-assemblies.md)
