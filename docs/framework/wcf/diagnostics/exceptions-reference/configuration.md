---
title: Konfiguracja
ms.date: 03/30/2017
ms.assetid: 86a6e12f-73b5-450e-8725-f4ca5fe0702c
ms.openlocfilehash: 3ef91a1f851f87ebf35669748f8beb1c6a880ae8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="configuration"></a>Konfiguracja
W tym temacie wymieniono wszystkie wyjątki generowane przez konfigurację usług Windows Communication Foundation (WCF).  
  
## <a name="exception-list"></a>Listy wyjątków  
  
|Kod zasobu|Ciąg zasobu|  
|-------------------|---------------------|  
|ConfigBindingCannotBeConfigured|Nie można skonfigurować powiązania w punkcie końcowym usługi.|  
|ConfigElementKeyNull|Klucz elementu określonej konfiguracji nie może mieć wartości null.|  
|ConfigExtensionTypeNotRegisteredInCollection|Typ określonego rozszerzenia nie jest zarejestrowany w kolekcji z określonym rozszerzeniem.|  
|ConfigIndexOutOfRange|Wartość określonego atrybutu jest poza zakresem.|  
|ConfigInvalidBindingConfigurationName|Określona konfiguracja nie ma powiązania o określonej nazwie.|  
|ConfigInvalidBindingName|Określona konfiguracja nie ma powiązania o określonej nazwie. To jest nieprawidłową wartością dla wiązania.|  
|ConfigInvalidCommonEndpointBehaviorType|Nie można dodać rozszerzenia określonego zachowania do wspólnego zachowania punktu końcowego, ponieważ nie obsługuje określonego typu.|  
|ConfigInvalidCommonServiceBehaviorType|Nie można dodać rozszerzenia określonego zachowania do wspólnego zachowania usługi, ponieważ nie obsługuje określonego typu.|  
|ConfigInvalidEndpointBehaviorType|Nie można dodać rozszerzenia zachowania określonych zachowanie określonego punktu końcowego, ponieważ podstawowy typ zachowania nie implementuje interfejsu IServiceBehavior.|  
|ConfigInvalidExtensionType|Określony typ musi pochodzić z określonym rozszerzeniem, do użycia w kolekcji.|  
|ConfigInvalidServiceBehaviorType|Nie można dodać rozszerzenia zachowania "do zachowania w przypadku specjalnej nazwy, ponieważ podstawowy typ zachowania nie implementuje interfejsu IServiceBehavior.|  
|ConfigMessageEncodingAlreadyInBinding|Nie można dodać elementu kodowania określonego komunikatu. Inny element kodowania komunikatu już istnieje w określonym powiązaniu. Może istnieć tylko jeden element dla każdego powiązania kodowania komunikatu.|  
|ConfigNoExtensionCollectionAssociatedWithType|Nie można odnaleźć kolekcji rozszerzeń skojarzonej z rozszerzeniem określonego typu.|  
|ConfigSectionNotFound|Nie można utworzyć sekcji określonej konfiguracji. Brak informacji w pliku Machine.config. Sprawdź, czy ta sekcja konfiguracji jest poprawnie zarejestrowana i czy zostały prawidłowo wpisana nazwa sekcji. Dla sekcji Windows Communication Foundation, uruchom ServiceModelReg.exe -i, aby naprawić ten błąd.|  
|ConfigTransportAlreadyInBinding|Nie można dodać elementu określonego transportu. Określone powiązanie już istnieje inny element transportu. Może istnieć tylko jeden element dla każdego powiązania kodowania komunikatu.|
