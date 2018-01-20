---
title: "Porady: instalowanie zestawu w globalnej pamięci podręcznej zestawów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- global assembly cache, installing assemblies
- Global Assembly Cache tool
ms.assetid: a7e6f091-d02c-49ba-b736-7295cb0eb743
caps.latest.revision: "24"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 98dd4d1e75fc37820a1b1f4eccfa48f978772687
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a>Porady: instalowanie zestawu w globalnej pamięci podręcznej zestawów
Istnieją dwa sposoby instalacji zestawu o silnej nazwie w globalnej pamięci podręcznej zestawów (GAC):  
  
> [!IMPORTANT]
>  W pamięci podręcznej GAC można instalować tylko zestawy o silnych nazwach. Aby uzyskać informacje o sposobie tworzenia zestawu z silną nazwą, zobacz [porady: podpisać zestaw o silnej nazwie](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).  
  
-   Przy użyciu [Instalatora Windows](http://msdn.microsoft.com/library/windows/desktop/cc185688.aspx).  
  
     Można to zrobić w programie Visual Studio 2012 i Visual Studio 2013, tworząc projekt programu InstallShield Limited Edition.  
  
     Jest to zalecany i najpopularniejszy sposób dodawania zestawów do globalnej pamięci podręcznej zestawów. Instalator oferuje funkcję zliczania odwołań do zestawów znajdujących się w globalnej pamięci podręcznej zestawów, a także zapewnia inne korzyści.  
  
-   Przy użyciu [narzędzie Global Assembly Cache (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).  
  
     Za pomocą narzędzia Gacutil.exe można dodawać zestawy o silnej nazwie do globalnej pamięci podręcznej zestawów i wyświetlać zawartość globalnej pamięci podręcznej zestawów.  
  
    > [!NOTE]
    >  Narzędzie Gacutil.exe jest przeznaczone tylko do celów deweloperskich i nie powinno być używane do instalowania zestawów produkcyjnych w globalnej pamięci podręcznej zestawów.  
  
> [!NOTE]
>  We wcześniejszych wersjach programu .NET Framework rozszerzenie powłoki Shfusion.dll Windows włączone do zainstalowania zestawy, przeciągając je w Eksploratorze plików. Począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], Shfusion.dll jest przestarzały.  
  
### <a name="to-use-the-global-assembly-cache-tool-gacutilexe"></a>Aby użyć narzędzia Globalna pamięć podręczna zestawów (Gacutil.exe).  
  
1.  W wierszu polecenia wpisz następujące polecenie:  
  
     **gacutil -i** \< *nazwy zestawu*>  
  
     W tym poleceniu *nazwy zestawu* jest nazwą zestawu do instalacji w globalnej pamięci podręcznej zestawów.  
  
 W poniższym przykładzie instalowana zestawu o nazwie pliku `hello.dll` w globalnej pamięci podręcznej zestawów.  
  
```  
gacutil -i hello.dll  
```  
  
 Aby uzyskać więcej informacji, zobacz [narzędzie Global Assembly Cache (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).  
  
### <a name="to-use-an-installshield-limited-edition-project"></a>Aby użyć projektu programu InstallShield Limited Edition  
  
1.  Dodawanie pakietu instalacji i wdrażania do rozwiązania Otwieranie menu skrótów do rozwiązania, a następnie wybierając **Dodaj**, **nowy projekt**.  
  
2.  W **Dodawanie nowego projektu** okna dialogowego, **zainstalowana** folderu, wybierz **inne typy projektów**, **instalacji i wdrażania**, **InstallShield Limited Edition**i nadaj nazwę projektu. (Jeśli zostanie wyświetlony monit, Pobierz, instalowania i aktywowania InstallShield.)  
  
3.  Wykonaj ogólne konfiguracji instalacji i wdrażania projektu przy użyciu Asystenta projektu w **Eksploratora rozwiązań**, lub wybierając podetapów numerowane czynności **Eksploratora rozwiązań**. Skonfiguruj ustawienia, jak w przypadku, jeśli nie dodawania zestawów w pamięci GAC.  
  
4.  Aby rozpocząć proces dodawania zestawu w GAC, wybierz **pliki**, znajduje się w **Określ dane aplikacji** krok **Eksploratora rozwiązań**.  
  
5.  W **folderów na komputerze docelowym** okienko, otwórz menu skrótów dla **komputera docelowego**, a następnie wybierz pozycję **Pokaż Folder wstępnie zdefiniowane**, **[ GlobalAssemblyCache]**.  
  
6.  Dla każdego projektu w rozwiązaniu zawierającym zestaw, który chcesz zainstalować w globalnej pamięci podręcznej zestawów:  
  
    1.  W **źródła folderów na komputerze** okienku wybierz projekt.  
  
    2.  W **folderów na komputerze docelowym** okienku wybierz **[GlobalAssemblyCache]**.  
  
    3.  W **komputera pliki źródłowe** okienku wybierz **podstawowe dane wyjściowe z** *< nazwa_projektu >*.  
  
    4.  Przeciągnij plik w kroku c do **plików na komputerze docelowym** okienka (lub użyj **kopiowania** i **Wklej** poleceń menu skrótów pliku).  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z zestawami i globalną pamięcią podręczną zestawów](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [Instrukcje: usuwanie zestawu z pamięci Global Assembly Cache](../../../docs/framework/app-domains/how-to-remove-an-assembly-from-the-gac.md)  
 [Gacutil.exe (narzędzie Global Assembly Cache)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)  
 [Instrukcje: podpisywanie zestawu silną nazwą](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)  
 [Wdrożenia Instalatora Windows](http://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0)
