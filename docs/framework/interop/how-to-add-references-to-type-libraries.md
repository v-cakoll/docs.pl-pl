---
title: 'Instrukcje: Dodawanie odwołań do bibliotek typów'
ms.date: 03/30/2017
helpviewer_keywords:
- importing type library
- interop assemblies, generating
- type libraries
- COM interop, importing type library
ms.assetid: f5cfa6ba-cc25-4017-82cd-ba7391859113
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4f0f254b7794ce1cd4c765bee70c78e3c60a14aa
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946492"
---
# <a name="how-to-add-references-to-type-libraries"></a>Instrukcje: Dodawanie odwołań do bibliotek typów
Program Visual Studio generuje zestaw międzyoperacyjny zawierający metadane podczas dodawania odwołania do biblioteki typów. Jeśli jest dostępny podstawowy zestaw międzyoperacyjny, program Visual Studio używa istniejącego zestawu przed wygenerowaniem nowego zestawu międzyoperacyjnego.  
  
### <a name="to-add-a-reference-to-a-type-library-in-visual-studio"></a>Aby dodać odwołanie do biblioteki typów w programie Visual Studio  
  
1. Zainstaluj plik DLL COM lub EXE na komputerze, chyba że plik Instalator systemu Windows. exe przeprowadzi instalację.  
  
2. Wybierz **projekt**, **Dodaj odwołanie**.  
  
3. W Menedżerze odwołań wybierz **com**.  
  
4. Wybierz bibliotekę typów z listy lub Wyszukaj plik. tlb.  
  
5. Wybierz **OK**.  
  
6. W Eksplorator rozwiązań otwórz menu skrótów dla właśnie dodanego odwołania, a następnie wybierz polecenie **Właściwości**.  
  
7. W oknie **Właściwości** upewnij się, że właściwość **Osadź typy** współdziałania ma **wartość true**. Powoduje to, że program Visual Studio osadzi informacje o typie dla typów COM w plikach wykonywalnych, eliminując konieczność wdrażania podstawowych zestawów międzyoperacyjnych w aplikacji.  
  
> [!NOTE]
> Opcje menu i okna dialogowego mogą się różnić w zależności od używanej wersji programu Visual Studio.  
  
### <a name="to-add-a-reference-to-a-type-library-for-command-line-compilation"></a>Aby dodać odwołanie do biblioteki typów dla kompilacji wiersza polecenia  
  
1. Generowanie zestawu międzyoperacyjnego zgodnie z opisem [w temacie How to: Generuj zestawy międzyoperacyjnych z](how-to-generate-interop-assemblies-from-type-libraries.md)bibliotek typów.  
  
2. Do osadzenia informacji o typie dla typów COM w plikach wykonywalnych Użyj opcji kompilatora [/link (C# opcje kompilatora)](../../csharp/language-reference/compiler-options/link-compiler-option.md) lub [/link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) z nazwą zestawu międzyoperacyjnego.  
  
## <a name="see-also"></a>Zobacz także

- [Importowanie biblioteki typów jako zestawu](importing-a-type-library-as-an-assembly.md)
- [Udostępnianie składników COM programowi .NET Framework](exposing-com-components.md)
- [Przewodnik: Osadzanie typów z zestawów zarządzanych w programie Visual StudioC#()](../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md) 
- [Przewodnik: Osadzanie typów z zestawów zarządzanych w programie Visual Studio (Visual Basic)](../../visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md)
- [/Link (C# opcje kompilatora)](../../csharp/language-reference/compiler-options/link-compiler-option.md)
- [/Link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md)
