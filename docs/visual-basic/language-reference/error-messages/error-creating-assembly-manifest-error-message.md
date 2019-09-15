---
title: 'Błąd podczas tworzenia manifestu zestawu: <error message>'
ms.date: 07/20/2015
f1_keywords:
- bc30140
- vbc30140
helpviewer_keywords:
- BC30140
ms.assetid: 1beb5aa0-7b79-4c85-946b-5c2d0a41d1d2
ms.openlocfilehash: 560635718a931cc9cdb687154a1d23970136de97
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972290"
---
# <a name="error-creating-assembly-manifest-error-message"></a>Wystąpił błąd podczas tworzenia \<manifestu zestawu: komunikat o błędzie >
Kompilator Visual Basic wywołuje Assembly Linker (Al.exe, znany także jako Alink) do generowania manifestu zestawu. Konsolidator zgłosił błąd w fazie wstępnej emisji tworzenia zestawu.  
  
 Taka sytuacja może wystąpić w przypadku problemów z plikiem klucza lub określonego kontenera kluczy. Aby w pełni podpisać zestaw, należy podać prawidłowy plik klucza zawierający informacje o kluczach publiczny i prywatny. Aby opóźnić podpisywanie zestawu, musisz zaznaczyć pole wyboru **Opóźnij tylko znak** i podać prawidłowy plik klucza, który zawiera informacje o kluczu publicznym. Klucz prywatny nie jest konieczny, gdy zestaw jest podpisany z opóźnieniem. Aby uzyskać więcej informacji, zobacz [jak: Podpisz zestaw silną nazwą](../../../standard/assembly/sign-strong-name.md).  
  
 **Identyfikator błędu:** BC30140  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Sprawdź komunikat o błędzie w cudzysłowach i zapoznaj się z tematem [Al.exe](../../../framework/tools/al-exe-assembly-linker.md). Aby uzyskać informacje o błędzie, AL1019 dalsze wyjaśnienie i porady  
  
2. Jeśli błąd będzie się powtarzać, należy zebrać informacje dotyczące okoliczności i powiadom pomoc techniczna firmy Microsoft.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Podpisz zestaw silną nazwą](../../../standard/assembly/sign-strong-name.md)
- [Strona podpisywania, Projektant projektu](/visualstudio/ide/reference/signing-page-project-designer)
- [Al.exe](../../../framework/tools/al-exe-assembly-linker.md)
- [Porozmawiaj z nami](/visualstudio/ide/talk-to-us)
