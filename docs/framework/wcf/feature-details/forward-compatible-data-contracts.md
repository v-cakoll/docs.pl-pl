---
title: Kontrakty danych zgodne z nowszymi wersjami
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], forward compatibility
ms.assetid: 413c9044-26f8-4ecb-968c-18495ea52cd9
ms.openlocfilehash: 34bde56b78ec0148cf6b924f8edd29343b97faa4
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597387"
---
# <a name="forward-compatible-data-contracts"></a>Kontrakty danych zgodne z nowszymi wersjami
Funkcja systemu kontraktów danych Windows Communication Foundation (WCF) polega na tym, że kontrakty mogą być rozwijane w czasie w sposób niepodzielony. Oznacza to, że klient ze starszą wersją kontraktu danych może komunikować się z usługą z nowszą wersją tego samego kontraktu danych lub klient z nowszą wersją kontraktu danych może komunikować się ze starszą wersją tego samego kontraktu danych. Aby uzyskać więcej informacji, zobacz [najlepsze rozwiązania: przechowywanie wersji kontraktu danych](../best-practices-data-contract-versioning.md).  
  
 Większość funkcji przechowywania wersji można zastosować w zależności od wymagań, gdy są tworzone nowe wersje istniejącego kontraktu danych. Jednak jedna funkcja *obsługi*wersji, która musi być wbudowana w typ z pierwszej wersji, aby działała prawidłowo.  
  
## <a name="round-tripping"></a>Dwukierunkowa  
 Gdy dane przechodzą z nowej wersji do starej wersji i z powrotem do nowej wersji kontraktu danych, nastąpi przekroczenie. Dwukierunkowa gwarancja gwarantuje, że żadne dane nie zostaną utracone. Włączenie operacji okrężnej powoduje, że typ do przodu jest zgodny z wszelkimi przyszłymi zmianami obsługiwanymi przez model przechowywania wersji kontraktu danych.  
  
 Aby włączyć funkcję okrężną dla określonego typu, typ musi implementować <xref:System.Runtime.Serialization.IExtensibleDataObject> interfejs. Interfejs zawiera jedną właściwość <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> (zwracającą <xref:System.Runtime.Serialization.ExtensionDataObject> Typ). Właściwość przechowuje wszystkie dane z przyszłych wersji kontraktu danych, które są nieznane w bieżącej wersji.  
  
### <a name="example"></a>Przykład  
 Następujący kontrakt danych nie jest zgodny ze zmianami w przyszłości.  
  
 [!code-csharp[C_DataContract#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#7)]
 [!code-vb[C_DataContract#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#7)]  
  
 Aby zapewnić zgodność typu z przyszłymi zmianami (np. dodaniem nowego elementu członkowskiego danych o nazwie "numer telefonu"), zaimplementuj <xref:System.Runtime.Serialization.IExtensibleDataObject> interfejs.  
  
 [!code-csharp[C_DataContract#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#8)]
 [!code-vb[C_DataContract#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#8)]  
  
 Gdy Infrastruktura WCF napotyka dane, które nie są częścią oryginalnego kontraktu danych, dane są przechowywane we właściwości i zachowywane. Nie jest on przetwarzany w żaden inny sposób, z wyjątkiem magazynu tymczasowego. Jeśli obiekt jest zwracany z powrotem do miejsca, w którym pochodzi, zwracane są również oryginalne (nieznane) dane. W związku z tym dane przeprowadzili rundy do i z punktu końcowego pochodzącego bez utraty. Należy jednak pamiętać, że jeśli źródłowy punkt końcowy wymaga przetworzenia danych, oczekiwany jest niewypełnienia, a punkt końcowy musi być w jakiś sposób wykrywany i uwzględniał zmianę.  
  
 <xref:System.Runtime.Serialization.ExtensionDataObject>Typ nie zawiera żadnych publicznych metod lub właściwości. Z tego względu nie można uzyskać bezpośredniego dostępu do danych przechowywanych wewnątrz <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> właściwości.  
  
 Funkcja okrężna może być wyłączona przez ustawienie `ignoreExtensionDataObject` `true` w <xref:System.Runtime.Serialization.DataContractSerializer> konstruktorze lub przez ustawienie <xref:System.ServiceModel.ServiceBehaviorAttribute.IgnoreExtensionDataObject%2A> właściwości na `true` <xref:System.ServiceModel.ServiceBehaviorAttribute> . Gdy ta funkcja jest wyłączona, Deserializator nie wypełni <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> właściwości i Serializator nie emituje zawartości właściwości.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.Serialization.IExtensibleDataObject>
- <xref:System.Runtime.Serialization.ExtensionDataObject>
- [Przechowywanie wersji kontraktów danych](data-contract-versioning.md)
- [Najlepsze rozwiązania: przechowywanie wersji kontraktów danych](../best-practices-data-contract-versioning.md)
