---
title: Wystąpił nieoczekiwany błąd, ponieważ zasób systemu operacyjnego zażądany dla uruchomienia pojedynczego wystąpienia nie może zostać pobrany
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_CantGetMemoryMappedFile
ms.assetid: 0d9f2a30-ff72-4355-8060-744f22339359
ms.openlocfilehash: 640e32dc7f748ecd0a999a8432512103f46862c2
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976174"
---
# <a name="an-unexpected-error-has-occurred-because-an-operating-system-resource-required-for-single-instance-startup-cannot-be-acquired"></a>Wystąpił nieoczekiwany błąd, ponieważ zasób systemu operacyjnego zażądany dla uruchomienia pojedynczego wystąpienia nie może zostać pobrany

Aplikacja nie może uzyskać wymaganego zasobu systemu operacyjnego. Oto niektóre z możliwych przyczyn tego problemu:  
  
- Aplikacja nie ma uprawnień do tworzenia nazwanych obiektów systemu operacyjnego.  
  
- Środowisko uruchomieniowe języka wspólnego nie ma uprawnień do tworzenia plików mapowanych na pamięć.  
  
- Aplikacja musi uzyskać dostęp do obiektu systemu operacyjnego, ale jest on używany przez inny proces.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Sprawdź, czy aplikacja ma wystarczające uprawnienia do tworzenia nazwanych obiektów systemu operacyjnego.  
  
2. Sprawdź, czy środowisko uruchomieniowe języka wspólnego ma wystarczające uprawnienia do tworzenia plików mapowanych na pamięć.  
  
3. Uruchom ponownie komputer, aby wyczyścić każdy proces, który może korzystać z zasobu potrzebnego do nawiązania połączenia z aplikacją oryginalnego wystąpienia.  
  
4. Zanotuj sytuacje, w których wystąpił błąd i Wywołaj usługi pomocy technicznej firmy Microsoft  
  
## <a name="see-also"></a>Zobacz także

- [Strona aplikacji, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [Podstawowe informacje o debugerze](/visualstudio/debugger/debugger-basics)
- [Porozmawiaj z nami](/visualstudio/ide/feedback-options)
