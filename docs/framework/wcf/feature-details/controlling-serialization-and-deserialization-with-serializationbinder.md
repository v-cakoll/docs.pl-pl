---
title: Kontrolowanie serializacji i deserializacji za pomocą elementu SerializationBinder
ms.date: 03/30/2017
ms.assetid: ba8dcecf-acc7-467c-939d-021bbac797d4
ms.openlocfilehash: 3252413606f4aaf45a825d8d0a6f4af8763ef6be
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33488920"
---
# <a name="controlling-serialization-and-deserialization-with-serializationbinder"></a>Kontrolowanie serializacji i deserializacji za pomocą elementu SerializationBinder
Podczas serializacji element formatujący przesyła informacje wymagane do utworzenia wystąpienia obiektu poprawnego typu i wersji. Informacje te obejmują zazwyczaj Pełna nazwa typu i nazwy zestawu obiektu. Domyślnie deserializacji używa tych informacji do utworzenia wystąpienia obiektu identyczne. W przypadku niektórych użytkowników może być konieczne do kontrolowania, która klasa w celu serializacji i deserializacji, albo ponieważ oryginalnej klasy mogą nie istnieć na komputerze wykonywania deserializacji, między zestawami przeniósł oryginalnej klasy lub inna wersja tej klasy jest wymagany na serwera i klienta. Aby uzyskać więcej informacji, zobacz [użycia wiążącego serializacji](../../../../docs/framework/wcf/samples/usage-of-serialization-binder.md).  
  
> [!WARNING]
>  Ta funkcja jest dostępna tylko w przypadku korzystania z <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> lub <xref:System.Runtime.Serialization.NetDataContractSerializer>.  
  
## <a name="using-serializationbinder"></a>Za pomocą elementu SerializationBinder  
 <xref:System.Runtime.Serialization.SerializationBinder>Klasa abstrakcyjna służy do kontroli rzeczywiste typy używane podczas serializacji i deserializacji. Aby kontrolować typów używany podczas serializacji i deserializacji, klasa wyprowadzona z <xref:System.Runtime.Serialization.SerializationBinder> i zastąpić <xref:System.Runtime.Serialization.SerializationBinder.BindToName(System.Type,System.String@,System.String@)> i <xref:System.Runtime.Serialization.SerializationBinder.BindToType(System.String,System.String)> metody. <xref:System.Runtime.Serialization.SerializationBinder.BindToName(System.Type,System.String@,System.String@)> Ma metody <xref:System.Type> i zwraca nazwę zestawu i typu. <xref:System.Runtime.Serialization.SerializationBinder.BindToType(System.String,System.String)> Metoda przyjmuje nazwę zestawu i typu i zwraca <xref:System.Type>.  
  
## <a name="see-also"></a>Zobacz też  
 [Serializacja i deserializacja](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md)  
 [Używanie obiektu wiążącego serializacji](../../../../docs/framework/wcf/samples/usage-of-serialization-binder.md)
