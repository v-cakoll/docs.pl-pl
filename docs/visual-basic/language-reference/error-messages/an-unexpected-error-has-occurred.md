---
title: "Wystąpił nieoczekiwany błąd, ponieważ zasób systemu operacyjnego zażądany dla uruchomienia pojedynczego wystąpienia nie może zostać pobrany"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrAppModel_CantGetMemoryMappedFile
ms.assetid: 0d9f2a30-ff72-4355-8060-744f22339359
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8969303d66e946d5579c6cca592b5701c4ebd632
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
