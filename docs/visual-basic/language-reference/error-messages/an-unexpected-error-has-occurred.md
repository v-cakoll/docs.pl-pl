---
title: Wystąpił nieoczekiwany błąd, ponieważ zasób systemu operacyjnego zażądany dla uruchomienia pojedynczego wystąpienia nie może zostać pobrany
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_CantGetMemoryMappedFile
ms.assetid: 0d9f2a30-ff72-4355-8060-744f22339359
ms.openlocfilehash: 82b513b89d661e49853e55f26df13eb354945038
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58828599"
---
# <a name="an-unexpected-error-has-occurred-because-an-operating-system-resource-required-for-single-instance-startup-cannot-be-acquired"></a>Wystąpił nieoczekiwany błąd, ponieważ zasób systemu operacyjnego zażądany dla uruchomienia pojedynczego wystąpienia nie może zostać pobrany
Aplikacja nie można uzyskać zasobu systemu operacyjnego wymagane. Możliwe przyczyny tego problemu, należą:  
  
-   Aplikacja nie ma uprawnień do utworzenia nazwane obiekty systemu operacyjnego.  
  
-   Środowisko uruchomieniowe języka wspólnego nie ma uprawnień, aby utworzyć pliki mapowane w pamięci.  
  
-   Aplikacja potrzebuje dostępu do obiektu systemu operacyjnego, ale jest używany przez inny proces.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Sprawdź, czy aplikacja ma wystarczające uprawnienia do tworzenia obiektów usługi o nazwie system operacyjny.  
  
2.  Sprawdź, czy środowisko uruchomieniowe języka wspólnego, ma wystarczające uprawnienia do tworzenia plików mapowanych na pamięć.  
  
3.  Uruchom ponownie komputer, aby wyczyścić każdy proces, który może używać zasobów wymaganych do połączenia do oryginalnego wystąpienia aplikacji.  
  
4.  Należy pamiętać, okoliczności, w których wystąpił błąd i wywołać pomoc techniczna firmy Microsoft  
  
## <a name="see-also"></a>Zobacz także

- [Strona aplikacji, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [Podstawowe informacje o debugerze](/visualstudio/debugger/debugger-basics)
- [Porozmawiaj z nami](/visualstudio/ide/talk-to-us)
