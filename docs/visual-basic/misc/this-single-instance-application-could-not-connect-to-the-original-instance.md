---
title: To pojedyncze wystąpienie aplikacji nie można połączyć z oryginalnego wystąpienia
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_SingleInstanceCantConnect
ms.assetid: 7c2c0cee-02a1-4157-be03-39d18e18408f
ms.openlocfilehash: 9bc1f33231cc4f29fabd100a695843beb334aeaa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33640257"
---
# <a name="this-single-instance-application-could-not-connect-to-the-original-instance"></a>To pojedyncze wystąpienie aplikacji nie można połączyć z oryginalnego wystąpienia
To pojedyncze wystąpienie aplikacji nie może połączyć się z wystąpieniem oryginalnym. Niektóre możliwe przyczyny tego problemu są następujące:  
  
-   Oryginalne wystąpienie przestał odpowiadać.  
  
-   Aplikacja nie ma uprawnień do tworzenia obiektów jądra. Aby uzyskać więcej informacji o obiektach jądra, zobacz [muteksy](../../standard/threading/mutexes.md).  
  
     Nazwę podstawową dla obiekt jądra pochodzi z łączenia GUID zestawu, numer wersji głównej i podrzędny numer wersji. Na przykład można podstawowej nazwy `3639f15d-9547-43da-8145-60da347829915.1`.  
  
## <a name="to-correct-this-error-when-developing-the-application"></a>Aby rozwiązać ten problem, podczas opracowywania aplikacji  
  
1.  Sprawdź, czy aplikacja nie przechodzi w stan, który nie odpowiada.  
  
2.  Sprawdź, czy aplikacja ma wystarczające uprawnienia do tworzenia obiektów jądra.  
  
3.  Ponowne uruchomienie oryginalnego wystąpienia aplikacji.  
  
4.  Uruchom ponownie komputer, aby wyczyścić żaden proces, który używa zasobu, który jest wymagany do połączenia do oryginalnego wystąpienia aplikacji.  
  
5.  Zanotuj okoliczności, w których wystąpił błąd, a telefonu pomocy technicznej firmy Microsoft.  
  
## <a name="see-also"></a>Zobacz też  
 [Podstawowe informacje o debugerze](/visualstudio/debugger/debugger-basics)  

