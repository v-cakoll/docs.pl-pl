---
title: Zestawy i Globalna pamięć podręczna zestawów (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fcf78ff1-f1ab-4a5d-b6d8-00d2046b6c80
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 893d869b1abaf9caa6f4705f40750912081d7df2
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="assemblies-and-the-global-assembly-cache-visual-basic"></a>Zestawy i Globalna pamięć podręczna zestawów (Visual Basic)
Zestawy stanowią podstawową jednostkę wdrożenia, kontroli wersji, ponownemu, zakresu aktywacji i uprawnień zabezpieczeń dla. Aplikacja Asp.net. Zestawy formę plik wykonywalny (.exe) lub dołączana dynamicznie biblioteka (dll) pliku i są blokami konstrukcyjnymi programu .NET Framework. Zawierają środowisko uruchomieniowe języka wspólnego o informacje, które należy znać typ implementacji. Można potraktować zestawu jako kolekcję typów i zasobów, które tworzą jednostkę logiczną funkcjonalności i są tworzone współdziałają ze sobą.  
  
 Zestawy mogą zawierać przynajmniej jeden moduł. Na przykład większych projektów mogą być planowane w taki sposób, że kilka indywidualnych deweloperów działać w oddzielnych modułów, wszystkie najbliższych, aby utworzyć w jednym zestawie. Aby uzyskać więcej informacji o modułach, zobacz temat [porady: tworzenie zestawów Multifile](../../../../framework/app-domains/how-to-build-a-multifile-assembly.md).  
  
 Zestawy mieć następujące właściwości:  
  
-   Zestawy są zaimplementowane jako pliki .exe lub dll.  
  
-   Można udostępniać zestawu między aplikacjami, ustawiając dla niego w globalnej pamięci podręcznej zestawów. Zestawy muszą być o silnych nazwach, aby mogły one zostać uwzględnione w globalnej pamięci podręcznej zestawów. Aby uzyskać więcej informacji, zobacz [zestawy Strong-Named](../../../../framework/app-domains/strong-named-assemblies.md).  
  
-   Zestawy są ładowane do pamięci tylko wtedy, jeśli są wymagane. Jeśli nie są używane, nie są załadowane. Oznacza to, że zestawy mogą być wydajnym sposobem zarządzania zasobami w większych projektów.  
  
-   Informacje o zestawie można uzyskać programistycznie przy użyciu odbicia. Aby uzyskać więcej informacji, zobacz [odbicie (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md).  
  
-   Jeśli do załadowania zestawu jedynie, aby sprawdzić, należy użyć metody takich jak <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A>.  
  
## <a name="assembly-manifest"></a>Manifest zestawu  
 W każdym zestawie jest *manifest zestawu*. Podobnie jak spisu treści, manifest zestawu zawiera następujące elementy:  
  
-   Tożsamość zestawu (jego nazwa i wersja).  
  
-   Tabela plików opisujące wszystkie pliki wchodzące w skład zestawu, na przykład innych zestawów utworzonego pliku .exe lub .dll opiera się na, lub nawet mapy bitowej i pliki Readme.  
  
-   *Lista odwołań zestawu*, który znajduje się lista wszystkich zależności zewnętrznych — biblioteki lub inne pliki wymagań aplikacji, które mogło zostać utworzone przez innego użytkownika. Odwołania do zestawów zawierają odwołania do obiektów zarówno globalnych, jak i prywatnych. Globalne obiekty znajdują się w globalnej pamięci podręcznej zestawów, dostępne dla innych aplikacji, w folderze System32 przypominające obszaru. <xref:Microsoft.VisualBasic?displayProperty=nameWithType> Przestrzeń nazw jest przykładem zestawu w globalnej pamięci podręcznej zestawów. Obiekty prywatne muszą być w katalogu albo poziomu jako lub poniżej katalogu, w którym jest zainstalowana aplikacja.  
  
 Ponieważ zestawy zawierają informacje o zawartości, przechowywanie wersji i zależności, aplikacje utworzone przy użyciu języka Visual Basic nie należy polegać na wartości rejestru systemu Windows w celu poprawnego działania. Zestawy zmniejszyć konflikty .dll i upewnić aplikacji, bardziej niezawodne i łatwiejsze do wdrożenia. W wielu przypadkach można zainstalować. Aplikacji opartej na sieci za pomocą kopiowania plików do komputera docelowego.  
  
 Aby uzyskać więcej informacji, zobacz [manifestu zestawu](../../../../framework/app-domains/assembly-manifest.md).  
  
## <a name="adding-a-reference-to-an-assembly"></a>Dodawanie odwołania do zestawu  
 Aby użyć zestawu, należy dodać odwołanie do niej. Następnie użyj [Imports — instrukcja](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) wybierz przestrzeń nazw elementów, którego chcesz użyć. Po odwołuje się do zestawu i zaimportowane, wszystkie dostępne klasy, właściwości, metody i inni członkowie ich przestrzenie nazw są dostępne dla aplikacji tak, jakby ich kodem należały pliku źródłowego.  
  
## <a name="creating-an-assembly"></a>Tworzenie zestawu  
 Kompilowanie aplikacji przez skompilowanie go z poziomu wiersza polecenia przy użyciu kompilatora wiersza polecenia. Aby uzyskać więcej informacji o tworzeniu zestawów z wiersza polecenia, zobacz [tworzenie z wiersza polecenia](../../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).  
  
> [!NOTE]
>  Tworzenie zestawu w programie Visual Studio na **kompilacji** menu wybierz **kompilacji**.  
  
## <a name="see-also"></a>Zobacz też  
 [Zestawy w środowisku uruchomieniowym CLR](../../../../framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 [Przyjazne zestawy (Visual Basic)](friend-assemblies.md)  
 [Porady: dzielenie się zestawem z innymi aplikacjami (Visual Basic)](how-to-share-an-assembly-with-other-applications.md)  
 [Porady: ładowanie i zwalnianie zestawów (Visual Basic)](how-to-load-and-unload-assemblies.md)  
 [Porady: Określanie, czy plik jest zestawem (Visual Basic)](how-to-determine-if-a-file-is-an-assembly.md)  
 [Porady: tworzenie i korzystanie z zestawów przy użyciu wiersza polecenia (Visual Basic)](how-to-create-and-use-assemblies-using-the-command-line.md)  
 [Wskazówki: Osadzanie typów z zarządzanych zestawów w programie Visual Studio (Visual Basic)](walkthrough-embedding-types-from-managed-assemblies-in-vs.md)  
 [Wskazówki: Osadzanie informacji o typie z zestawów Microsoft Office w Visual Studio (Visual Basic)](walkthrough-embedding-type-information-from-microsoft-office-assemblies-in-vs.md)
