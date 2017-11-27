---
title: "Zestawy i Globalna pamięć podręczna zestawów (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 149f5ca5-5b34-4746-9542-1ae43b2d0256
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3743c07f1de1d39f07d559aa161e4547422a6e52
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="assemblies-and-the-global-assembly-cache-c"></a>Zestawy i Globalna pamięć podręczna zestawów (C#)
Zestawy stanowią podstawową jednostkę wdrożenia, kontroli wersji, ponownemu, zakresu aktywacji i uprawnień zabezpieczeń dla. Aplikacja Asp.net. Zestawy formę plik wykonywalny (.exe) lub dołączana dynamicznie biblioteka (dll) pliku i są blokami konstrukcyjnymi programu .NET Framework. Zawierają środowisko uruchomieniowe języka wspólnego o informacje, które należy znać typ implementacji. Można potraktować zestawu jako kolekcję typów i zasobów, które tworzą jednostkę logiczną funkcjonalności i są tworzone współdziałają ze sobą.  
  
 Zestawy mogą zawierać przynajmniej jeden moduł. Na przykład większych projektów mogą być planowane w taki sposób, że kilka indywidualnych deweloperów działać w oddzielnych modułów, wszystkie najbliższych, aby utworzyć w jednym zestawie. Aby uzyskać więcej informacji o modułach, zobacz temat [porady: tworzenie zestawów Multifile](https://msdn.microsoft.com/library/226t7yxe).  
  
 Zestawy mieć następujące właściwości:  
  
-   Zestawy są zaimplementowane jako pliki .exe lub dll.  
  
-   Można udostępniać zestawu między aplikacjami, ustawiając dla niego w globalnej pamięci podręcznej zestawów. Zestawy muszą być o silnych nazwach, aby mogły one zostać uwzględnione w globalnej pamięci podręcznej zestawów. Aby uzyskać więcej informacji, zobacz [zestawy Strong-Named](https://msdn.microsoft.com/library/wd40t7ad).  
  
-   Zestawy są ładowane do pamięci tylko wtedy, jeśli są wymagane. Jeśli nie są używane, nie są załadowane. Oznacza to, że zestawy mogą być wydajnym sposobem zarządzania zasobami w większych projektów.  
  
-   Informacje o zestawie można uzyskać programistycznie przy użyciu odbicia. Aby uzyskać więcej informacji, zobacz [odbicia (C#)](../../../../csharp/programming-guide/concepts/reflection.md).  
  
-   Jeśli do załadowania zestawu jedynie, aby sprawdzić, należy użyć metody takich jak <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A>.  
  
## <a name="assembly-manifest"></a>Manifest zestawu  
 W każdym zestawie jest *manifest zestawu*. Podobnie jak spisu treści, manifest zestawu zawiera następujące elementy:  
  
-   Tożsamość zestawu (jego nazwa i wersja).  
  
-   Tabela plików opisujące wszystkie pliki wchodzące w skład zestawu, na przykład innych zestawów utworzonego pliku .exe lub .dll opiera się na, lub nawet mapy bitowej i pliki Readme.  
  
-   *Lista odwołań zestawu*, który znajduje się lista wszystkich zależności zewnętrznych — biblioteki lub inne pliki wymagań aplikacji, które mogło zostać utworzone przez innego użytkownika. Odwołania do zestawów zawierają odwołania do obiektów zarówno globalnych, jak i prywatnych. Globalne obiekty znajdują się w globalnej pamięci podręcznej zestawów, obszar dostępne dla innych aplikacji. Obiekty prywatne muszą być w katalogu albo poziomu jako lub poniżej katalogu, w którym jest zainstalowana aplikacja.  
  
 Ponieważ zestawy zawierają informacje o zawartości, przechowywanie wersji i zależności, aplikacje utworzone przy użyciu języka C# nie należy polegać na wartości rejestru systemu Windows w celu poprawnego działania. Zestawy zmniejszyć konflikty .dll i upewnić aplikacji, bardziej niezawodne i łatwiejsze do wdrożenia. W wielu przypadkach można zainstalować. Aplikacji opartej na sieci za pomocą kopiowania plików do komputera docelowego.  
  
 Aby uzyskać więcej informacji, zobacz [manifestu zestawu](https://msdn.microsoft.com/library/1w45z383).  
  
## <a name="adding-a-reference-to-an-assembly"></a>Dodawanie odwołania do zestawu  
 Aby użyć zestawu, należy dodać odwołanie do niej. Następnie użyj [dyrektywa using](../../../../csharp/language-reference/keywords/using-directive.md) wybierz przestrzeń nazw elementów, którego chcesz użyć. Po odwołuje się do zestawu i zaimportowane, wszystkie dostępne klasy, właściwości, metody i inni członkowie ich przestrzenie nazw są dostępne dla aplikacji tak, jakby ich kodem należały pliku źródłowego.  
  
 W języku C# umożliwia także dwie wersje tego samego zestawu w pojedynczej aplikacji. Aby uzyskać więcej informacji, zobacz [alias zewnętrzny](../../../../csharp/language-reference/keywords/extern-alias.md).  
  
## <a name="creating-an-assembly"></a>Tworzenie zestawu  
 Skompiluj aplikację, klikając **kompilacji** na **kompilacji** menu lub przez skompilowanie go z poziomu wiersza polecenia przy użyciu kompilatora wiersza polecenia. Aby uzyskać więcej informacji o tworzeniu zestawów z wiersza polecenia, zobacz [kompilowania z wiersza polecenia csc.exe](../../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).  
  
> [!NOTE]
>  Tworzenie zestawu w programie Visual Studio na **kompilacji** menu wybierz **kompilacji**.  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../../csharp/programming-guide/index.md)  
 [Zestawy w środowisko uruchomieniowe języka wspólnego](https://msdn.microsoft.com/library/k3677y81)  
 [Przyjazne zestawy (C#)](friend-assemblies.md)  
 [Porady: dzielenie się zestawem z innymi aplikacjami (C#)](how-to-share-an-assembly-with-other-applications.md)  
 [Porady: ładowanie i zwalnianie zestawów (C#)](how-to-load-and-unload-assemblies.md)  
 [Porady: Określanie, czy plik jest zestawem (C#)](how-to-determine-if-a-file-is-an-assembly.md)  
 [Porady: tworzenie i korzystanie z zestawów przy użyciu wiersza polecenia (C#)](how-to-create-and-use-assemblies-using-the-command-line.md)  
 [Wskazówki: Osadzanie typów z zarządzanych zestawów w programie Visual Studio (C#)](walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)  
 [Wskazówki: Osadzanie informacji o typie z zestawów Microsoft Office w Visual Studio (C#)](walkthrough-embedding-type-information-from-microsoft-office-assemblies.md)
