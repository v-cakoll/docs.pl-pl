---
title: 'Błąd podczas tworzenia manifestu zestawu: <error message>'
ms.date: 07/20/2015
f1_keywords:
- bc30140
- vbc30140
helpviewer_keywords:
- BC30140
ms.assetid: 1beb5aa0-7b79-4c85-946b-5c2d0a41d1d2
ms.openlocfilehash: 0f67b772bab3104c00510954d01b200aadfa9e8a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59296293"
---
# <a name="error-creating-assembly-manifest-error-message"></a>Wystąpił błąd podczas tworzenia manifestu zestawu: \<komunikat o błędzie >
Kompilator Visual Basic wywołuje Assembly Linker (Al.exe, znany także jako Alink) do generowania manifestu zestawu. Konsolidator zgłosił błąd podczas etapu emisji wstępnego tworzenia zestawu.  
  
 Może to wystąpić, jeśli występują problemy z pliku klucza lub określony kontener kluczy. Aby w pełni Podpisz zestaw, należy podać prawidłowy plik klucza, który zawiera informacje o kluczach publicznych i prywatnych. Aby opóźnić Podpisz zestaw, należy wybrać **opóźnienie logowania tylko** pole wyboru, a następnie podaj prawidłowy plik klucza, który zawiera informacje o informacje o kluczu publicznym. Klucz prywatny nie jest konieczne w przypadku, gdy zestaw jest podpisany z opóźnieniem. Aby uzyskać więcej informacji, zobacz [jak: Podpisywanie zestawu silną nazwą](../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).  
  
 **Identyfikator błędu:** BC30140  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Sprawdź komunikat o błędzie w cudzysłowach i zapoznaj się z tematem [Al.exe](../../../framework/tools/al-exe-assembly-linker.md). Aby uzyskać dalsze wyjaśnienie błędu AL1019 i porady  
  
2. Jeśli błąd będzie się powtarzać, należy zebrać informacje dotyczące okoliczności i powiadom pomoc techniczna firmy Microsoft.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Podpisywanie zestawu silną nazwą](../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)
- [Strona podpisywania, Projektant projektu](/visualstudio/ide/reference/signing-page-project-designer)
- [Al.exe](../../../framework/tools/al-exe-assembly-linker.md)
- [Porozmawiaj z nami](/visualstudio/ide/talk-to-us)
