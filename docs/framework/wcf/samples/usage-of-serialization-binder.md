---
title: Używanie obiektu wiążącego serializacji
ms.date: 03/30/2017
ms.assetid: ab46c087-200c-45bf-9c95-5a6cda6e8b98
ms.openlocfilehash: bfce2a14c8757250c520919c8ff2a4d7048a9d5c
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2019
ms.locfileid: "74138646"
---
# <a name="usage-of-serialization-binder"></a>Używanie obiektu wiążącego serializacji
Ten przykład pokazuje, jak za pomocą <xref:System.Runtime.Serialization.SerializationBinder> zmienić wersję typu ogólnego podczas serializacji.  
  
## <a name="demonstrates"></a>Demonstracje  
 <xref:System.Runtime.Serialization.SerializationBinder>, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>  
  
## <a name="discussion"></a>Dyskusji  
 Ten przykład pokazuje, jak dwie jednostki, które są ukierunkowane na różne wersje .NET Framework mogą komunikować się przy użyciu binarnego programu formatującego i spinacza serializacji.  
  
Ten przykład został opracowany przy użyciu usług zdalnych platformy .NET. Składa się ona z serwera docelowego .NET Framework 4, który implementuje kontrakt z typami ogólnymi i dwóch różnych klientów, jeden element docelowy .NET Framework 2,0 i inny element docelowy .NET Framework 4.  
  
 Serwer dołącza <xref:System.Runtime.Serialization.SerializationBinder> do pliku binarnego programu formatującego, aby można było zmienić wersję typów odpowiednio dla serializacji, tak aby obaj klienci mogli prawidłowo deserializować te typy.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Aby wykonać klienta, kliknij prawym przyciskiem myszy rozwiązanie, SBGenericsVTS (6 projektów), a następnie wybierz polecenie **Właściwości**.  
  
2. W obszarze **wspólne właściwości**wybierz pozycję **projekt startowy**, a następnie wybierz opcję **wiele projektów startowych**.  
  
3. Najpierw wybierz **serwer** , a następnie **Client20** , a następnie **Client40**. Wybierz akcję **Rozpocznij** dla tych trzech projektów i pozostaw wartość nie ustawiony na **none**.  
  
4. Kliknij przycisk **OK** , a następnie naciśnij klawisz F5, aby uruchomić przykład.
