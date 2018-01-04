---
title: "To pojedyncze wystąpienie aplikacji nie można połączyć z oryginalnego wystąpienia"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrAppModel_SingleInstanceCantConnect
ms.assetid: 7c2c0cee-02a1-4157-be03-39d18e18408f
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9cb8cef696ba93f922dfe0d92195a5fb5147b4cc
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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

