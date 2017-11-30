---
title: "Porady: dodawanie odwołań do bibliotek typów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- importing type library
- interop assemblies, generating
- type libraries
- COM interop, importing type library
ms.assetid: f5cfa6ba-cc25-4017-82cd-ba7391859113
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e5bbc99c3c40b0864a7c1c25cb79a3d7c26e3a86
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-references-to-type-libraries"></a>Porady: dodawanie odwołań do bibliotek typów
Program Visual Studio generuje zestawu międzyoperacyjnego zawierający metadane, podczas dodawania odwołania do biblioteki typów. Jeśli podstawowy zestaw międzyoperacyjny jest dostępny, Visual Studio korzysta z istniejącego zestawu przed wygenerowaniem nowego zestawu międzyoperacyjnego.  
  
### <a name="to-add-a-reference-to-a-type-library-in-visual-studio"></a>Aby dodać odwołanie do biblioteki typów w programie Visual Studio  
  
1.  Zainstaluj plik COM DLL lub EXE na komputerze, chyba, że plik Windows Setup.exe przeprowadza instalację.  
  
2.  Wybierz **projektu**, **Dodaj odwołanie**.  
  
3.  W Menedżerze odwołania, zaznacz opcję **COM**.  
  
4.  Wybierz bibliotekę typów, z listy lub Przeglądaj w poszukiwaniu pliku .tlb.  
  
5.  Wybierz **OK**.  
  
6.  W Eksploratorze rozwiązań Otwórz menu skrótów dla odwołania został właśnie dodany, a następnie wybierz pozycję **właściwości**.  
  
7.  W **właściwości** okna, upewnij się, że **Osadź typy międzyoperacyjne** właściwość jest ustawiona na **True**. Powoduje osadzanie informacji o typie dla typów COM w plikach wykonywalnych, eliminując konieczność wdrożenia podstawowe zestawy międzyoperacyjne z aplikacją programu Visual Studio.  
  
> [!NOTE]
>  Menu i opcje okna dialogowego może się różnić w zależności od wersji programu Visual Studio używasz.  
  
### <a name="to-add-a-reference-to-a-type-library-for-command-line-compilation"></a>Aby dodać odwołanie do biblioteki typów dla kompilacji wiersza polecenia  
  
1.  Generowanie zestawu międzyoperacyjnego, zgodnie z opisem w [porady: generowanie zestawy międzyoperacyjne z bibliotek typów](../../../docs/framework/interop/how-to-generate-interop-assemblies-from-type-libraries.md).  
  
2.  Użyj [/Link (opcje kompilatora C#)](~/docs/csharp/language-reference/compiler-options/link-compiler-option.md) lub [/Link (Visual Basic)](~/docs/visual-basic/reference/command-line-compiler/link.md) typy — opcja kompilatora o nazwie zestawu międzyoperacyjnego osadzanie informacji o typie dla modelu COM w Twoje pliki wykonywalne.  
  
## <a name="see-also"></a>Zobacz też  
 [Importowanie biblioteki typów jako zestawu](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md)  
 [Udostępnianie składników modelu COM aplikacji .NET Framework](../../../docs/framework/interop/exposing-com-components.md)  
 [Wskazówki: Osadzanie informacji o typie z zestawów Microsoft Office](http://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3)  
 [Wskazówki: Osadzanie typów z zarządzanych zestawów](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21)  
 [/ Link (opcje kompilatora C#)](~/docs/csharp/language-reference/compiler-options/link-compiler-option.md)  
 [/ Link (Visual Basic)](~/docs/visual-basic/reference/command-line-compiler/link.md)
