---
title: 'Porady: instalowanie zestawu w globalnej pamięci podręcznej zestawów'
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- global assembly cache, installing assemblies
- Global Assembly Cache tool
ms.assetid: a7e6f091-d02c-49ba-b736-7295cb0eb743
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8c3bd568cf504125bc99801815d08764417b42cd
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2018
ms.locfileid: "43469001"
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a>Porady: instalowanie zestawu w globalnej pamięci podręcznej zestawów
Istnieją dwa sposoby instalacji zestawu o silnej nazwie w globalnej pamięci podręcznej zestawów (GAC):  
  
> [!IMPORTANT]
>  W pamięci podręcznej GAC można instalować tylko zestawy o silnych nazwach. Aby uzyskać informacje o sposobie tworzenia zestawu z silną nazwą, zobacz [porady: podpisywanie zestawu za pomocą silnej nazwy](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).  
  
-   Za pomocą [Instalatora Windows](/windows/desktop/Msi/windows-installer-portal).  
  
     Można to zrobić w programie Visual Studio 2012 i Visual Studio 2013, tworząc projekt programu InstallShield Limited Edition.  
  
     Jest to zalecany i najpopularniejszy sposób dodawania zestawów do globalnej pamięci podręcznej zestawów. Instalator oferuje funkcję zliczania odwołań do zestawów znajdujących się w globalnej pamięci podręcznej zestawów, a także zapewnia inne korzyści.  
  
-   Za pomocą [narzędzia Globalna pamięć podręczna zestawów (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).  
  
     Za pomocą narzędzia Gacutil.exe można dodawać zestawy o silnej nazwie do globalnej pamięci podręcznej zestawów i wyświetlać zawartość globalnej pamięci podręcznej zestawów.  
  
    > [!NOTE]
    >  Narzędzie Gacutil.exe jest przeznaczone tylko do celów deweloperskich i nie powinno być używane do instalowania zestawów produkcyjnych w globalnej pamięci podręcznej zestawów.  
  
> [!NOTE]
>  We wcześniejszych wersjach programu .NET Framework rozszerzenie powłoki Windows Shfusion.dll umożliwia instalowanie zestawów, przeciągając je w Eksploratorze plików. Począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], biblioteka Shfusion.dll jest przestarzała.  
  
### <a name="to-use-the-global-assembly-cache-tool-gacutilexe"></a>Aby użyć narzędzia Globalna pamięć podręczna zestawów (Gacutil.exe).  
  
1.  W wierszu polecenia wpisz następujące polecenie:  
  
     **gacutil -i** \< *nazwy zestawu*>  
  
     W tym poleceniu *nazwy zestawu* to nazwa zestawu, aby zainstalować w globalnej pamięci podręcznej.  
  
 Poniższy przykład instaluje zestaw o nazwie pliku `hello.dll` w globalnej pamięci podręcznej.  
  
```  
gacutil -i hello.dll  
```  
  
 Aby uzyskać więcej informacji, zobacz [narzędzia Globalna pamięć podręczna zestawów (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).  
  
### <a name="to-use-an-installshield-limited-edition-project"></a>Aby użyć projektu programu InstallShield Limited Edition  
  
1.  Dodaj do rozwiązania pakiet instalacji i wdrożenia, otwierając menu skrótów dla danego rozwiązania, a następnie wybierając **Dodaj**, **nowy projekt**.  
  
2.  W **Dodaj nowy projekt** dialogowym **zainstalowane** folderu, wybierz **inne typy projektów**, **instalacja i wdrożenie**, **InstallShield Limited Edition**, a następnie nadaj projektowi nazwę. (Jeśli zostanie wyświetlony monit, pobierania, instalowania i aktywowania InstallShield.)  
  
3.  Wykonaj ogólną konfigurację projektu instalacji i wdrożenia przy użyciu Asystenta projektu w **Eksploratora rozwiązań**, lub wybierając podkroki ponumerowanych kroków w **Eksploratora rozwiązań**. Skonfiguruj ustawienia, jak gdyby były nie dodaje zestawy w pamięci GAC.  
  
4.  Aby rozpocząć proces dodawania zestawu do globalnej pamięci podręcznej zestawów, wybierz pozycję **pliki**, czyli w ramach **Określ dane aplikacji** krok w **Eksploratora rozwiązań**.  
  
5.  W **foldery komputera docelowego** okienko, otwórz menu skrótów dla **komputera docelowego**, a następnie wybierz **Pokaż wstępnie zdefiniowany Folder**, **[ GlobalAssemblyCache]**.  
  
6.  Dla każdego projektu w rozwiązaniu zawierającym zestaw, który chcesz zainstalować w globalnej pamięci podręcznej zestawów:  
  
    1.  W **foldery komputera źródłowego** okienku, wybierz projekt.  
  
    2.  W **foldery komputera docelowego** okienku wybierz **[GlobalAssemblyCache]**.  
  
    3.  W **komputera pliki źródłowe** okienku wybierz **podstawowe wyjście z** *< project_name >*.  
  
    4.  Przeciągnij plik z kroku c do **plikach na komputerze docelowym** okienko (lub użyj **kopiowania** i **Wklej** poleceń w menu skrótów pliku).  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z zestawami i globalną pamięcią podręczną zestawów](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [Instrukcje: usuwanie zestawu z pamięci Global Assembly Cache](../../../docs/framework/app-domains/how-to-remove-an-assembly-from-the-gac.md)  
 [Gacutil.exe (narzędzie Global Assembly Cache)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)  
 [Instrukcje: podpisywanie zestawu silną nazwą](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)  
 [Wdrażanie za pomocą Instalatora Windows](https://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0)
