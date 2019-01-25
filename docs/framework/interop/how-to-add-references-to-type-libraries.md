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
ms.openlocfilehash: ebd7599205206e026c7de7b4e7bc2e5352771bd5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54522222"
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
- [Przewodnik: Osadzanie informacji o typie z zestawów Microsoft Office](https://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3(v=vs.100))
- [Przewodnik: Osadzanie typów z zarządzanych zestawów](https://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21)
- [/ Link (opcje kompilatora C#)](../../csharp/language-reference/compiler-options/link-compiler-option.md)
- [/ Link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md)
