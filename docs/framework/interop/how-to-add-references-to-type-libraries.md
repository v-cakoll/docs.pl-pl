---
title: 'Porady: dodawanie odwołań do bibliotek typów'
ms.date: 03/30/2017
helpviewer_keywords:
- importing type library
- interop assemblies, generating
- type libraries
- COM interop, importing type library
ms.assetid: f5cfa6ba-cc25-4017-82cd-ba7391859113
ms.openlocfilehash: 1e82a499b77cc6d1d49eaf13e243201bbdc4c5fe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181442"
---
# <a name="how-to-add-references-to-type-libraries"></a>Porady: dodawanie odwołań do bibliotek typów
Visual Studio generuje zestaw interop zawierający metadane podczas dodawania odwołania do biblioteki typów. Jeśli podstawowy zestaw międzyoperacyjny jest dostępny, Visual Studio używa istniejącego zestawu przed wygenerowaniem nowego zestawu międzyoperacyjnego.  
  
### <a name="to-add-a-reference-to-a-type-library-in-visual-studio"></a>Aby dodać odwołanie do biblioteki typów w programie Visual Studio  
  
1. Zainstaluj plik BIBLIOTEKI DLL lub EXE COM na komputerze, chyba że plik Setup.exe systemu Windows wykona instalację.  
  
2. Wybierz **polecenie Projekt**, Dodaj **odwołanie**.  
  
3. W Menedżerze odwołań wybierz pozycję **COM**.  
  
4. Wybierz bibliotekę typów z listy lub wyszukaj plik .tlb.  
  
5. Wybierz pozycję **OK**.  
  
6. W Eksploratorze rozwiązań otwórz menu skrótów dla właśnie dodanego odniesienia, a następnie wybierz polecenie **Właściwości**.  
  
7. W oknie **Właściwości** upewnij się, że właściwość **Osadzanie typów międzyop jest** ustawiona na **Wartość True**. Powoduje to, że program Visual Studio osadza informacje o typie dla typów COM w plikach wykonywalnych, eliminując konieczność wdrażania podstawowych zestawów międzyoperacyjnych za pomocą aplikacji.  
  
> [!NOTE]
> Opcje menu i okna dialogowego mogą się różnić w zależności od używanej wersji programu Visual Studio.  
  
### <a name="to-add-a-reference-to-a-type-library-for-command-line-compilation"></a>Aby dodać odwołanie do biblioteki typów dla kompilacji wiersza polecenia  
  
1. Generowanie zestawu międzyoperacyjnego zgodnie z opisem w [jak: Generowanie zestawów międzyoperacyjnych z bibliotek typów](how-to-generate-interop-assemblies-from-type-libraries.md).  
  
2. Użyj opcji [kompilatora -link (C# Compiler Options)](../../csharp/language-reference/compiler-options/link-compiler-option.md) lub [-link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) o nazwie zestawu interop, aby osadzić informacje o typie dla typów COM w plikach wykonywalnych.  
  
## <a name="see-also"></a>Zobacz też

- [Importowanie biblioteki typów jako zestawu](importing-a-type-library-as-an-assembly.md)
- [Udostępnianie składników COM programowi.NET Framework](exposing-com-components.md)
- [Przewodnik: osadzanie typów z zarządzanych zestawów w programie Visual Studio](../../standard/assembly/embed-types-visual-studio.md)
- [-link (Opcje kompilatora języka C#)](../../csharp/language-reference/compiler-options/link-compiler-option.md)
- [-link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md)
