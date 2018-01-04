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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ba2140459c0b571e9b35824d3dba274e8447ac40
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="controlling-serialization-and-deserialization-with-serializationbinder"></a>Kontrolowanie serializacji i deserializacji za pomocą elementu SerializationBinder
Podczas serializacji element formatujący przesyła informacje wymagane do utworzenia wystąpienia obiektu poprawnego typu i wersji. Informacje te obejmują zazwyczaj Pełna nazwa typu i nazwy zestawu obiektu. Domyślnie deserializacji używa tych informacji do utworzenia wystąpienia obiektu identyczne. W przypadku niektórych użytkowników może być konieczne do kontrolowania, która klasa w celu serializacji i deserializacji, albo ponieważ oryginalnej klasy mogą nie istnieć na komputerze wykonywania deserializacji, między zestawami przeniósł oryginalnej klasy lub inna wersja tej klasy jest wymagany na serwera i klienta. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Używanie obiektu wiążącego serializacji](../../../../docs/framework/wcf/samples/usage-of-serialization-binder.md).  
  
> [!WARNING]
>  Ta funkcja jest dostępna tylko w przypadku korzystania z <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> lub <xref:System.Runtime.Serialization.NetDataContractSerializer>.  
  
## <a name="using-serializationbinder"></a>Za pomocą elementu SerializationBinder  
 <xref:System.Runtime.Serialization.SerializationBinder>Klasa abstrakcyjna służy do kontroli rzeczywiste typy używane podczas serializacji i deserializacji. Aby kontrolować typów używany podczas serializacji i deserializacji, klasa wyprowadzona z <xref:System.Runtime.Serialization.SerializationBinder> i zastąpić <xref:System.Runtime.Serialization.SerializationBinder.BindToName(System.Type,System.String@,System.String@)> i <xref:System.Runtime.Serialization.SerializationBinder.BindToType(System.String,System.String)> metody. <xref:System.Runtime.Serialization.SerializationBinder.BindToName(System.Type,System.String@,System.String@)> Ma metody <xref:System.Type> i zwraca nazwę zestawu i typu. <xref:System.Runtime.Serialization.SerializationBinder.BindToType(System.String,System.String)> Metoda przyjmuje nazwę zestawu i typu i zwraca <xref:System.Type>.  
  
## <a name="see-also"></a>Zobacz też  
 [Serializacja i deserializacja](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md)  
 [Używanie obiektu wiążącego serializacji](../../../../docs/framework/wcf/samples/usage-of-serialization-binder.md)
