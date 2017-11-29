---
title: "Kontrolowanie serializacji i deserializacji za pomocą elementu SerializationBinder"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba8dcecf-acc7-467c-939d-021bbac797d4
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1c3180d62824f94e27e02c80e09fdf32252f0a23
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="controlling-serialization-and-deserialization-with-serializationbinder"></a>Kontrolowanie serializacji i deserializacji za pomocą elementu SerializationBinder
Podczas serializacji element formatujący przesyła informacje wymagane do utworzenia wystąpienia obiektu poprawnego typu i wersji. Informacje te obejmują zazwyczaj Pełna nazwa typu i nazwy zestawu obiektu. Domyślnie deserializacji używa tych informacji do utworzenia wystąpienia obiektu identyczne. W przypadku niektórych użytkowników może być konieczne do kontrolowania, która klasa w celu serializacji i deserializacji, albo ponieważ oryginalnej klasy mogą nie istnieć na komputerze wykonywania deserializacji, między zestawami przeniósł oryginalnej klasy lub inna wersja tej klasy jest wymagany na serwera i klienta. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Używanie obiektu wiążącego serializacji](../../../../docs/framework/wcf/samples/usage-of-serialization-binder.md).  
  
> [!WARNING]
>  Ta funkcja jest dostępna tylko w przypadku korzystania z <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> lub <xref:System.Runtime.Serialization.NetDataContractSerializer>.  
  
## <a name="using-serializationbinder"></a>Za pomocą elementu SerializationBinder  
 <xref:System.Runtime.Serialization.SerializationBinder>Klasa abstrakcyjna służy do kontroli rzeczywiste typy używane podczas serializacji i deserializacji. Aby kontrolować typów używany podczas serializacji i deserializacji, klasa wyprowadzona z <xref:System.Runtime.Serialization.SerializationBinder> i zastąpić <xref:System.Runtime.Serialization.SerializationBinder.BindToName%2A> System.String, System.String)?qualifyHint=False & autoUpgrade = True i <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> System.String)? qualifyHint = False & autoUpgrade = True metody. <xref:System.Runtime.Serialization.SerializationBinder.BindToName%2A> System.String, System.String)?qualifyHint=False & autoUpgrade = ma wartość True, Metoda <xref:System.Type> i zwraca nazwę zestawu i typu. <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> System.String)?qualifyHint=False & autoUpgrade = ma wartość True, metoda zestawu i nazwa typu i zwraca <xref:System.Type>.  
  
## <a name="see-also"></a>Zobacz też  
 [Serializacja i deserializacja](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md)  
 [Używanie obiektu wiążącego serializacji](../../../../docs/framework/wcf/samples/usage-of-serialization-binder.md)
