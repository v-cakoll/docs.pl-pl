---
title: Używanie obiektu wiążącego serializacji
ms.date: 03/30/2017
ms.assetid: ab46c087-200c-45bf-9c95-5a6cda6e8b98
ms.openlocfilehash: 677decebcf444fed95311bd02acf8a96e0a4eca9
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591781"
---
# <a name="usage-of-serialization-binder"></a>Używanie obiektu wiążącego serializacji
Ten przykład ilustruje sposób używania <xref:System.Runtime.Serialization.SerializationBinder> Aby zmienić wersję typu ogólnego, gdy jest serializowana.  
  
## <a name="demonstrates"></a>Demonstracje  
 <xref:System.Runtime.Serialization.SerializationBinder>, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>  
  
## <a name="discussion"></a>Dyskusja  
 Niniejszy przykład pokazuje jak dwie jednostki, że są określania wartości docelowej różne wersje usługi .NET Framework mogą komunikować się za pomocą binarny program formatujący i integratora serializacji.  
  
 Rozwój w tym przykładzie zostały wykonane przy użyciu wywołaniem funkcji zdalnych .NET. Przykład składa się z serwerem określania wartości docelowej [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)], który implementuje kontrakt typy ogólne i dwóch różnych klientów, jeden dla [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)] i ustawianie elementów docelowych innej [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)].  
  
 Dołącza serwera <xref:System.Runtime.Serialization.SerializationBinder> do binarny program formatujący, aby można było zmienić wersję typy odpowiednio na serializacji, więc obaj klienci może wykonywać deserializację tych typów prawidłowo.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1. Aby wykonać klienta, kliknij prawym przyciskiem myszy rozwiązanie, SBGenericsVTS (6 projekty), a następnie wybierz **właściwości**.  
  
2. W **wspólne właściwości**, wybierz opcję **projekt startowy**, a następnie wybierz **wiele projektów startowych**.  
  
3. Wybierz **serwera** pierwszy, następnie **Client20** i następnie **Client40**. Wybierz **Start** działanie tych trzech projektów oraz pozostawienie pozostałych równa **Brak**.  
  
4. Kliknij przycisk **OK** a następnie naciśnij klawisz F5, aby uruchomić próbki.
