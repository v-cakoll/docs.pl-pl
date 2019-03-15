---
title: Ta aplikacja o pojedynczym wystąpieniu nie można połączyć z oryginalnego wystąpienia
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_SingleInstanceCantConnect
ms.assetid: 7c2c0cee-02a1-4157-be03-39d18e18408f
ms.openlocfilehash: 241ad5b9986e78f88ab5ca39bc73f7372162ba76
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2019
ms.locfileid: "58037504"
---
# <a name="this-single-instance-application-could-not-connect-to-the-original-instance"></a>Ta aplikacja o pojedynczym wystąpieniu nie można połączyć z oryginalnego wystąpienia
Ta aplikacja o pojedynczym wystąpieniu nie może połączyć do oryginalnego wystąpienia. Niektóre z możliwych przyczyn tego problemu są następujące:  
  
-   Oryginalne wystąpienie przestał odpowiadać.  
  
-   Aplikacja nie ma uprawnień do tworzenia obiektów jądra. Aby uzyskać więcej informacji na temat jądra obiektów, zobacz [muteksy](../../standard/threading/mutexes.md).  
  
     Nazwa podstawowa dla obiektów jądra pochodzi z łączenia identyfikator GUID, główny numer wersji i pomocniczy numer wersji zestawu. Na przykład może być nazwa podstawowa `3639f15d-9547-43da-8145-60da347829915.1`.  
  
## <a name="to-correct-this-error-when-developing-the-application"></a>Aby naprawić ten błąd, podczas opracowywania aplikacji  
  
1.  Upewnij się, że aplikacja nie przechodzi do stanu nie odpowiada.  
  
2.  Sprawdź, czy aplikacja ma wystarczające uprawnienia do tworzenia obiektów jądra.  
  
3.  Uruchom ponownie oryginalne wystąpienie aplikacji.  
  
4.  Uruchom ponownie komputer, aby wyczyścić każdy proces, który może używać zasób, który jest wymagane do połączenia z oryginalnej aplikacji wystąpienia.  
  
5.  Należy pamiętać, okoliczności, w których wystąpił błąd i telefoniczna pomoc techniczna firmy Microsoft.  
  
## <a name="see-also"></a>Zobacz także

- [Podstawowe informacje o debugerze](/visualstudio/debugger/debugger-basics)
