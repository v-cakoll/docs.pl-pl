---
title: Wystąpił nieoczekiwany błąd, ponieważ zasób systemu operacyjnego zażądany dla uruchomienia pojedynczego wystąpienia nie może zostać pobrany
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_CantGetMemoryMappedFile
ms.assetid: 0d9f2a30-ff72-4355-8060-744f22339359
ms.openlocfilehash: 313128d5511ddd0f3b75c58e2c10a74eb967d130
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33587655"
---
# <a name="an-unexpected-error-has-occurred-because-an-operating-system-resource-required-for-single-instance-startup-cannot-be-acquired"></a>Wystąpił nieoczekiwany błąd, ponieważ zasób systemu operacyjnego zażądany dla uruchomienia pojedynczego wystąpienia nie może zostać pobrany
Aplikacji nie można uzyskać zasobu niezbędne systemu operacyjnego. Niektóre możliwe przyczyny tego problemu są:  
  
-   Aplikacja nie ma uprawnień do tworzenia nazwanych obiektów systemu operacyjnego.  
  
-   Środowisko uruchomieniowe języka wspólnego nie ma uprawnień do tworzenia plików mapowanych na pamięć.  
  
-   Aplikacja potrzebuje dostępu do obiektu systemu operacyjnego, ale używa on innego procesu.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Sprawdź, czy aplikacja ma wystarczające uprawnienia do tworzenia nazwanych obiektów systemu operacyjnego.  
  
2.  Sprawdź, czy środowisko uruchomieniowe języka wspólnego ma wystarczające uprawnienia do tworzenia plików mapowanych na pamięć.  
  
3.  Uruchom ponownie komputer, aby wyczyścić żaden proces, który używa zasobów wymaganych do połączenia do oryginalnego wystąpienia aplikacji.  
  
4.  Zanotuj okoliczności, w których wystąpił błąd, a następnie wywołać pomocy technicznej firmy Microsoft  
  
## <a name="see-also"></a>Zobacz też  
 [Strona aplikacji, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)  
 [Podstawowe informacje o debugerze](/visualstudio/debugger/debugger-basics)  
 [Porozmawiaj z nami](/visualstudio/ide/talk-to-us)
