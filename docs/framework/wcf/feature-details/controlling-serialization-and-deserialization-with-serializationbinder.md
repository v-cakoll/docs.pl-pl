---
title: Kontrolowanie serializacji i deserializacji za pomocą elementu SerializationBinder
ms.date: 03/30/2017
ms.assetid: ba8dcecf-acc7-467c-939d-021bbac797d4
ms.openlocfilehash: cb2476b55a965e326e492c3c0b77f0be65b2b290
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61857262"
---
# <a name="controlling-serialization-and-deserialization-with-serializationbinder"></a>Kontrolowanie serializacji i deserializacji za pomocą elementu SerializationBinder
Podczas serializacji element formatujący przesyła informacje wymagane do utworzenia wystąpienia obiektu poprawnego typu i wersji. Informacje te obejmują zazwyczaj Pełna nazwa typu i nazwy zestawu obiektu. Domyślnie deserializacji używa tych informacji w celu utworzenia wystąpienia obiektu identyczne. Niektórzy użytkownicy może być konieczne do kontrolowania której klasy do serializacji i deserializacji, albo ponieważ oryginalnej klasy nie może istnieć na komputerze wykonywania deserializacji, oryginalnym klasy przeniósł między zestawami, lub w nieco innej klasy serwer i klienta. Aby uzyskać więcej informacji, zobacz [użycia wiążącego serializacji](../../../../docs/framework/wcf/samples/usage-of-serialization-binder.md).  
  
> [!WARNING]
>  Ta funkcja jest dostępna tylko w przypadku korzystania z <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> lub <xref:System.Runtime.Serialization.NetDataContractSerializer>.  
  
## <a name="using-serializationbinder"></a>Za pomocą pomocą elementu SerializationBinder  
 <xref:System.Runtime.Serialization.SerializationBinder> Klasa abstrakcyjna służy do kontroli rzeczywiste typy używane podczas serializacji i deserializacji. Aby kontrolować typy używane podczas serializacji i deserializacji, należy wyprowadzić klasę z <xref:System.Runtime.Serialization.SerializationBinder> i zastąpić <xref:System.Runtime.Serialization.SerializationBinder.BindToName(System.Type,System.String@,System.String@)> i <xref:System.Runtime.Serialization.SerializationBinder.BindToType(System.String,System.String)> metody. <xref:System.Runtime.Serialization.SerializationBinder.BindToName(System.Type,System.String@,System.String@)> Metoda przyjmuje <xref:System.Type> i zwraca nazwę zestawu i typu. <xref:System.Runtime.Serialization.SerializationBinder.BindToType(System.String,System.String)> Metoda przyjmuje nazwę zestawu i typu i zwraca <xref:System.Type>.  
  
## <a name="see-also"></a>Zobacz także

- [Serializacja i deserializacja](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md)
- [Używanie obiektu wiążącego serializacji](../../../../docs/framework/wcf/samples/usage-of-serialization-binder.md)
