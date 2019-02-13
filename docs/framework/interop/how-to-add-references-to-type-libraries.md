---
title: 'Instrukcje: Dodaj odwołania do bibliotek typów'
ms.date: 03/30/2017
helpviewer_keywords:
- importing type library
- interop assemblies, generating
- type libraries
- COM interop, importing type library
ms.assetid: f5cfa6ba-cc25-4017-82cd-ba7391859113
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 71c2a6b183890aa9625dcffbef59d14c27ebe754
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/13/2019
ms.locfileid: "56219403"
---
# <a name="how-to-add-references-to-type-libraries"></a>Instrukcje: Dodaj odwołania do bibliotek typów
Program Visual Studio generuje zestaw międzyoperacyjny zawierający metadane, gdy użytkownik dodaje odnośnik do biblioteki typów. Jeśli podstawowy zestaw międzyoperacyjny jest dostępny, Visual Studio korzysta z istniejącego zestawu przed wygenerowaniem nowego zestawu międzyoperacyjnego.  
  
### <a name="to-add-a-reference-to-a-type-library-in-visual-studio"></a>Aby dodać odwołanie do biblioteki typów w programie Visual Studio  
  
1.  Zainstaluj plik COM DLL lub EXE na komputerze, chyba, że plik Windows Setup.exe wykonuje instalację.  
  
2.  Wybierz **projektu**, **Dodaj odwołanie**.  
  
3.  Wybierz w Menedżerze odwołań **COM**.  
  
4.  Wybierz bibliotekę typów, z listy lub Przeglądaj w poszukiwaniu pliku .tlb.  
  
5.  Wybierz **OK**.  
  
6.  W Eksploratorze rozwiązań Otwórz menu skrótów dla odwołania do właśnie dodane, a następnie wybierz **właściwości**.  
  
7.  W **właściwości** okna, upewnij się, że **Osadź typy współdziałania** właściwość jest ustawiona na **True**. To powoduje, że Visual Studio w celu osadzenia informacji o typie dla typów modelu COM w plikach wykonywalnych, eliminując konieczność wdrażania podstawowych zestawów międzyoperacyjnych z aplikacją.  
  
> [!NOTE]
>  Okno dialogowe i menu opcji w oknie mogą się różnić w zależności od wersji programu Visual Studio jest używany.  
  
### <a name="to-add-a-reference-to-a-type-library-for-command-line-compilation"></a>Aby dodać odwołanie do biblioteki typów dla kompilacji wiersza polecenia  
  
1.  Generowanie zestawu międzyoperacyjnego, zgodnie z opisem w [jak: Generowanie zestawów międzyoperacyjnych z bibliotek typów](how-to-generate-interop-assemblies-from-type-libraries.md).  
  
2.  Użyj [/link (C# opcje kompilatora)](../../csharp/language-reference/compiler-options/link-compiler-option.md) lub [/Link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) — opcja kompilatora z nazwą zestawu międzyoperacyjnego do osadzenia informacji o typie dla modelu COM, typy w swoje pliki wykonywalne.  
  
## <a name="see-also"></a>Zobacz także
- [Importowanie biblioteki typów jako zestawu](importing-a-type-library-as-an-assembly.md)
- [Udostępnianie składników COM programowi .NET Framework](exposing-com-components.md)
- [Przewodnik: Osadzanie informacji o typie z zestawów Microsoft Office w programie Visual Studio (C#)](../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-type-information-from-microsoft-office-assemblies.md)
- [Przewodnik: Osadzanie informacji o typie z zestawów Microsoft Office w programie Visual Studio (Visual Basic)](../../visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-type-information-from-microsoft-office-assemblies-in-vs.md)
- [Przewodnik: Osadzanie typów z zarządzanych zestawów w programie Visual Studio (C#)](/docs/csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md) 
- [Przewodnik: Osadzanie typów z zarządzanych zestawów w programie Visual Studio (Visual Basic)](/docs/visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md)
- [/ Link (opcje kompilatora C#)](../../csharp/language-reference/compiler-options/link-compiler-option.md)
- [/ Link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md)
