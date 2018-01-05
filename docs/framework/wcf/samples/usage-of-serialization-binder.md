---
title: "Używanie obiektu wiążącego serializacji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ab46c087-200c-45bf-9c95-5a6cda6e8b98
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: be6ce62722c0d1bd18122496312c3a55241a8fbb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="usage-of-serialization-binder"></a>Używanie obiektu wiążącego serializacji
Ten przykład przedstawia sposób użycia <xref:System.Runtime.Serialization.SerializationBinder> Aby zmienić wersję typu ogólnego, gdy jest on serializowany.  
  
## <a name="demonstrates"></a>Demonstracje  
 <xref:System.Runtime.Serialization.SerializationBinder>, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>  
  
## <a name="discussion"></a>Omówienie  
 W tym przykładzie pokazano, jak dwie jednostki, które są przeznaczonych dla różnych wersji programu [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] może komunikować się za pomocą binarnego elementu formatującego i wiążącego serializacji.  
  
 Rozwój tego przykładu zostały wykonane przy użyciu funkcji zdalnych .NET. Próbka składa się z serwerem przeznaczonych dla [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)], który implementuje kontrakt typy ogólne i dwóch różnych klientów, co przeznaczonych dla [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)] i przeznaczonych dla innej [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)].  
  
 Dołącza serwera <xref:System.Runtime.Serialization.SerializationBinder> do binarne programu formatującego, aby można było zmienić wersję typy odpowiednio na serializacji, więc obaj klienci może wykonywać deserializację typu poprawnie.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie próbki  
  
1.  Do wykonania klienta, kliknij prawym przyciskiem myszy rozwiązanie, SBGenericsVTS (projekty 6), a następnie wybierz **właściwości**.  
  
2.  W **wspólne właściwości**, wybierz pozycję **projekt startowy**, a następnie wybierz pozycję **wiele projektów startowych**.  
  
3.  Wybierz **serwera** pierwszy, a następnie **Client20** , a następnie **Client40**. Wybierz **Start** działania te trzy projekty i pozostawić rest ustawioną **Brak**.  
  
4.  Kliknij przycisk **OK** , a następnie naciśnij klawisz F5, aby uruchomić próbki.
