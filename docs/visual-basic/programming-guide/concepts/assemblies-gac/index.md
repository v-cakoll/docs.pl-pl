---
title: Zestawy i Globalna pamięć podręczna zestawów (Visual Basic)
ms.date: 07/20/2015
ms.assetid: fcf78ff1-f1ab-4a5d-b6d8-00d2046b6c80
ms.openlocfilehash: 413d3266546fa1d2b403509793c62e76bca5bc70
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54717262"
---
# <a name="assemblies-and-the-global-assembly-cache-visual-basic"></a>Zestawy i Globalna pamięć podręczna zestawów (Visual Basic)
Zespoły tworzą podstawową jednostką wdrażania, kontroli wersji, ponownego użycia, określania zakresu aktywacji i uprawnień zabezpieczeń. Aplikacja oparta na sieci. Zestawy formę dołączana dynamicznie biblioteka (dll) pliku lub plik wykonywalny (.exe) i są blokami konstrukcyjnymi programu .NET Framework. Zapewniają one środowiska uruchomieniowego języka wspólnego informacje, które musi być znane implementacje typu. Można potraktować zestawu jako kolekcję typów i zasobów, które tworzą jednostkę logiczną funkcji i zostały opracowane w celu współpracują ze sobą.  
  
 Zespoły mogą zawierać przynajmniej jeden moduł. Na przykład większe projekty mogą być planowane w taki sposób, że kilka indywidualnych deweloperów działać na osobne moduły, wszystkie nadchodzące ze sobą, aby utworzyć pojedynczy zestaw. Aby uzyskać więcej informacji na temat modułów, zobacz temat [jak: Kompilacja zestawów wieloplikowych](../../../../framework/app-domains/how-to-build-a-multifile-assembly.md).  
  
 Zestawy mają następujące właściwości:  
  
-   Zestawy są implementowane jako pliki .exe lub .dll.  
  
-   Można udostępniać między aplikacjami przez umieszczenie go w globalnej pamięci podręcznej zestawu. Zestawy muszą być o silnej nazwie aby mogły zostać uwzględnione w globalnej pamięci podręcznej. Aby uzyskać więcej informacji, zobacz [zestawy Strong-Named](../../../../framework/app-domains/strong-named-assemblies.md).  
  
-   Zestawy są ładowane do pamięci tylko wtedy, jeśli są one wymagane. Jeśli nie są one używane, nie są one załadowane. Oznacza to, że zestawy może być wydajnym sposobem zarządzania zasobami w dużych projektach.  
  
-   Informacje o zestawie można uzyskać programistycznie przy użyciu odbicia. Aby uzyskać więcej informacji, zobacz [odbicie (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md).  
  
-   Jeśli do załadowania zestawu tylko, aby sprawdzić, należy użyć metody takie jak <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A>.  
  
## <a name="assembly-manifest"></a>Manifest zestawu  
 W ramach każdego zestawu jest *manifestu zestawu*. Podobnie jak w spisie treści, manifest zestawu zawiera następujące informacje:  
  
-   Tożsamość zestawu (jego nazwa i wersja).  
  
-   Tabela plików opisujące wszystkie pliki wchodzące w skład zestawu, na przykład innych zestawów utworzonych, plik .exe lub .dll opiera się na, lub nawet mapy bitowej i pliki Readme.  
  
-   *Listę odwołań zestawu*, który znajduje się lista wszystkich zależności zewnętrznych — dll debuggle lub inne pliki do potrzeb aplikacji, które mogą zostać utworzone przez inną osobę. Odwołania do zestawów zawierają odwołania do obiektów globalnych i prywatnych. Obiekty globalne znajdują się w globalnej pamięci podręcznej, obszaru, które są dostępne dla innych aplikacji, przypominające katalogu System32. <xref:Microsoft.VisualBasic?displayProperty=nameWithType> Przestrzeni nazw jest przykładem zestawu w globalnej pamięci podręcznej. Obiekty prywatne musi znajdować się w katalogu na poziomie tym samym poziomie, jak i poniżej katalogu, w którym jest zainstalowana aplikacja.  
  
 Ponieważ zestawy zawierają informacje o zawartości, przechowywanie wersji i zależności, aplikacji, utworzonej za pomocą Visual Basic nie należy polegać na wartości rejestru Windows, aby działać prawidłowo. Zestawy zmniejszyć konflikty .dll i dzięki którym Twoje aplikacje bardziej niezawodne i łatwiejsze do wdrożenia. W wielu przypadkach można zainstalować. Aplikacja oparta na sieci poprzez kopiowaniem plików do komputera docelowego.  
  
 Aby uzyskać więcej informacji, zobacz [manifestu zestawu](../../../../framework/app-domains/assembly-manifest.md).  
  
## <a name="adding-a-reference-to-an-assembly"></a>Dodawanie odwołania do zestawu  
 Aby korzystać z zestawu, należy dodać odwołanie do niej. Następnie użyj [Imports — instrukcja](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) wybrać przestrzeń nazw elementów, w której chcesz użyć. Gdy odwołanie do zestawu i zaimportowaniu wszystkich dostępnych klas, właściwości, metod i inni członkowie jej przestrzenie nazw są dostępne dla aplikacji tak, jakby ich kod były częścią pliku źródłowego.  
  
## <a name="creating-an-assembly"></a>Tworzenie zestawu  
 Skompiluj aplikację, tworząc go w wierszu polecenia za pomocą kompilatora wiersza polecenia. Aby uzyskać szczegółowe informacje o tworzeniu zestawów z wiersza polecenia, zobacz [tworzenie z wiersza polecenia](../../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).  
  
> [!NOTE]
>  Tworzenie zestawu w programie Visual Studio na **kompilacji** menu wybierz opcję **kompilacji**.  
  
## <a name="see-also"></a>Zobacz także
- [Zestawy w środowisku uruchomieniowym CLR](../../../../framework/app-domains/assemblies-in-the-common-language-runtime.md)
- [Przyjazne zestawy (Visual Basic)](friend-assemblies.md)
- [Instrukcje: Dzielenie się zestawem z innymi aplikacjami (Visual Basic)](how-to-share-an-assembly-with-other-applications.md)
- [Instrukcje: Ładowanie i zwalnianie zestawów (Visual Basic)](how-to-load-and-unload-assemblies.md)
- [Instrukcje: Określić, czy plik jest zestawem (Visual Basic)](how-to-determine-if-a-file-is-an-assembly.md)
- [Instrukcje: Tworzenie i używanie zestawów przy użyciu wiersza polecenia (Visual Basic)](how-to-create-and-use-assemblies-using-the-command-line.md)
- [Przewodnik: Osadzanie typów z zarządzanych zestawów w programie Visual Studio (Visual Basic)](walkthrough-embedding-types-from-managed-assemblies-in-vs.md)
- [Przewodnik: Osadzanie informacji o typie z zestawów Microsoft Office w programie Visual Studio (Visual Basic)](walkthrough-embedding-type-information-from-microsoft-office-assemblies-in-vs.md)
