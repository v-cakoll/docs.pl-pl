---
title: Ta aplikacja z jednym wystąpieniem nie może nawiązać połączenia z oryginalnym wystąpieniem
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_SingleInstanceCantConnect
ms.assetid: 7c2c0cee-02a1-4157-be03-39d18e18408f
ms.openlocfilehash: 04ceec4839d07ba959c39af8c4f582c7abfe7d6b
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198130"
---
# <a name="this-single-instance-application-could-not-connect-to-the-original-instance"></a>Ta aplikacja z jednym wystąpieniem nie może nawiązać połączenia z oryginalnym wystąpieniem
Ta aplikacja pojedynczego wystąpienia nie może nawiązać połączenia z oryginalnym wystąpieniem. Poniżej przedstawiono niektóre możliwe przyczyny tego problemu:  
  
- Oryginalne wystąpienie przestało odpowiadać.  
  
- Aplikacja nie ma uprawnień do tworzenia obiektów jądra. Aby uzyskać więcej informacji na temat obiektów jądra, zobacz [muteksy](../../standard/threading/mutexes.md).  
  
     Nazwa podstawowa obiektów jądra pochodzi z łączenia identyfikatora GUID zestawu, głównego numeru wersji i pomocniczego numeru wersji. Na przykład nazwa podstawowa może być `3639f15d-9547-43da-8145-60da347829915.1`.  
  
## <a name="to-correct-this-error-when-developing-the-application"></a>Aby poprawić ten błąd podczas tworzenia aplikacji  
  
1. Sprawdź, czy aplikacja nie przechodzi w stan braku odpowiedzi.  
  
2. Sprawdź, czy aplikacja ma wystarczające uprawnienia do tworzenia obiektów jądra.  
  
3. Uruchom ponownie oryginalne wystąpienie aplikacji.  
  
4. Uruchom ponownie komputer, aby wyczyścić każdy proces, który może korzystać z zasobu, który jest wymagany do nawiązania połączenia z aplikacją oryginalnego wystąpienia.  
  
5. Zanotuj sytuacje, w których wystąpił błąd, i telefoniczne usługi pomocy technicznej firmy Microsoft.  
  
## <a name="see-also"></a>Zobacz także

- [Podstawowe informacje o debugerze](/visualstudio/debugger/debugger-feature-tour)
