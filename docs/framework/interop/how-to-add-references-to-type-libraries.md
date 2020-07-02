---
title: 'Instrukcje: Dodawanie odwołań do bibliotek typów'
description: Zapoznaj się z tematem Dodawanie odwołań do bibliotek typów w programie Visual Studio lub dla kompilacji wiersza polecenia.
ms.date: 03/30/2017
helpviewer_keywords:
- importing type library
- interop assemblies, generating
- type libraries
- COM interop, importing type library
ms.assetid: f5cfa6ba-cc25-4017-82cd-ba7391859113
ms.openlocfilehash: a3c24385c9cc7debe95aa10369b050897415bc46
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617434"
---
# <a name="how-to-add-references-to-type-libraries"></a>Instrukcje: Dodawanie odwołań do bibliotek typów
Program Visual Studio generuje zestaw międzyoperacyjny zawierający metadane podczas dodawania odwołania do biblioteki typów. Jeśli jest dostępny podstawowy zestaw międzyoperacyjny, program Visual Studio używa istniejącego zestawu przed wygenerowaniem nowego zestawu międzyoperacyjnego.  
  
### <a name="to-add-a-reference-to-a-type-library-in-visual-studio"></a>Aby dodać odwołanie do biblioteki typów w programie Visual Studio  
  
1. Zainstaluj plik DLL COM lub EXE na komputerze, chyba że plik Setup.exe systemu Windows przeprowadzi instalację.  
  
2. Wybierz **projekt**, **Dodaj odwołanie**.  
  
3. W Menedżerze odwołań wybierz **com**.  
  
4. Wybierz bibliotekę typów z listy lub Wyszukaj plik. tlb.  
  
5. Wybierz przycisk **OK**.  
  
6. W Eksplorator rozwiązań otwórz menu skrótów dla właśnie dodanego odwołania, a następnie wybierz polecenie **Właściwości**.  
  
7. W oknie **Właściwości** upewnij się, że właściwość **Osadź typy** współdziałania ma **wartość true**. Powoduje to, że program Visual Studio osadzi informacje o typie dla typów COM w plikach wykonywalnych, eliminując konieczność wdrażania podstawowych zestawów międzyoperacyjnych w aplikacji.  
  
> [!NOTE]
> Opcje menu i okna dialogowego mogą się różnić w zależności od używanej wersji programu Visual Studio.  
  
### <a name="to-add-a-reference-to-a-type-library-for-command-line-compilation"></a>Aby dodać odwołanie do biblioteki typów dla kompilacji wiersza polecenia  
  
1. Generowanie zestawu międzyoperacyjnego zgodnie z opisem w temacie [How to: Generate Assembly Interop from Library Type](how-to-generate-interop-assemblies-from-type-libraries.md)librarys.  
  
2. Użyj opcji [-link (opcje kompilatora C#)](../../csharp/language-reference/compiler-options/link-compiler-option.md) lub [-link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) z nazwą zestawu międzyoperacyjnego, aby osadzić informacje o typie dla typów com w plikach wykonywalnych.  
  
## <a name="see-also"></a>Zobacz także

- [Importowanie biblioteki typów jako zestawu](importing-a-type-library-as-an-assembly.md)
- [Udostępnianie składników COM programowi.NET Framework](exposing-com-components.md)
- [Przewodnik: osadzanie typów z zarządzanych zestawów w programie Visual Studio](../../standard/assembly/embed-types-visual-studio.md)
- [-Link (opcje kompilatora C#)](../../csharp/language-reference/compiler-options/link-compiler-option.md)
- [-Link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md)
