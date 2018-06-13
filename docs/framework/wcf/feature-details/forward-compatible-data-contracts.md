---
title: Kontrakty danych zgodne z nowszymi wersjami
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], forward compatibility
ms.assetid: 413c9044-26f8-4ecb-968c-18495ea52cd9
ms.openlocfilehash: 95a72d5d09538bc6f663f2376c7f8f928909cd57
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33492209"
---
# <a name="forward-compatible-data-contracts"></a>Kontrakty danych zgodne z nowszymi wersjami
Funkcja programu Windows Communication Foundation (WCF) jest system kontraktu danych który umów można rozwijać w czasie nierozdzielający sposoby. Oznacza to, że klienta przy użyciu starszej wersji kontraktu danych może komunikować się z usługą przy użyciu nowszej wersji tego samego kontraktu danych lub klienta przy użyciu nowszej wersji kontraktu danych może komunikować się ze starszą wersją tej samej kontraktu danych. Aby uzyskać więcej informacji, zobacz [najlepsze rozwiązania: przechowywanie wersji kontraktów danych](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md).  
  
 Większość funkcji przechowywania wersji można stosować na zgodnie z potrzebami, podczas tworzenia nowych wersji istniejących kontraktu danych. Jednak jedna z funkcji przechowywania wersji, *dwustronną komunikację*, muszą zostać skompilowane na typ z pierwszej wersji prawidłowego funkcjonowania.  
  
## <a name="round-tripping"></a>Dwustronną komunikację  
 Dwustronną komunikację występuje, gdy dane są przesyłane z nowej wersji na starszą wersję i z powrotem do nowej wersji kontraktu danych. Dwustronną komunikację gwarantuje, że żadne dane nie są tracone. Włączanie dwustronną komunikację sprawia, że typ zgodne z nowszymi o zmianach w przyszłości obsługiwane przez model przechowywanie wersji kontraktu danych.  
  
 Aby włączyć dwustronną komunikację dla określonego typu, typ musi implementować <xref:System.Runtime.Serialization.IExtensibleDataObject> interfejsu. Interfejs zawiera jedną właściwość <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> (zwracanie <xref:System.Runtime.Serialization.ExtensionDataObject> typu). Właściwość przechowuje wszystkie dane z przyszłych wersji kontraktu danych, który jest nieznany w bieżącej wersji.  
  
### <a name="example"></a>Przykład  
 Następujące kontraktu danych nie jest zgodne z nowszymi z przyszłe zmiany.  
  
 [!code-csharp[C_DataContract#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#7)]
 [!code-vb[C_DataContract#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#7)]  
  
 Aby typ zgodny z przyszłe zmiany (takich jak dodawanie nowego elementu członkowskiego danych o nazwie "phoneNumber"), należy zaimplementować <xref:System.Runtime.Serialization.IExtensibleDataObject> interfejsu.  
  
 [!code-csharp[C_DataContract#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#8)]
 [!code-vb[C_DataContract#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#8)]  
  
 Jeśli infrastruktura WCF napotka dane, które nie jest częścią kontrakt danych, dane są przechowywane we właściwości i zachowane. Nie został przetworzony w inny sposób, z wyjątkiem magazynu tymczasowego. Jeśli obiekt jest zwracany do pochodzenie, jest także zwracany oryginalnych danych (nieznany). W związku z tym dane wprowadził obiegu do i z punktem końcowym źródłowego bez utraty. Należy jednak pamiętać, że w razie potrzeby danych do przetwarzania źródłowego punktu końcowego tego oczekuje się unmet i punkt końcowy musi jakiś sposób wykrywania i wprowadzać zmiany.  
  
 <xref:System.Runtime.Serialization.ExtensionDataObject> Typ nie zawiera publicznej metody lub właściwości. W związku z tym nie można uzyskać bezpośredni dostęp do danych przechowywanych w <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> właściwości.  
  
 Funkcja dwustronną komunikację może zostać wyłączony, albo ustawiając `ignoreExtensionDataObject` do `true` w <xref:System.Runtime.Serialization.DataContractSerializer> konstruktora lub przez ustawienie <xref:System.ServiceModel.ServiceBehaviorAttribute.IgnoreExtensionDataObject%2A> właściwości `true` na <xref:System.ServiceModel.ServiceBehaviorAttribute>. Jeśli ta funkcja jest wyłączona, Deserializator nie spowoduje wypełnienie <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> właściwości i Serializator nie Emituj treści właściwości.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.Serialization.IExtensibleDataObject>  
 <xref:System.Runtime.Serialization.ExtensionDataObject>  
 [Przechowywanie wersji kontraktów danych](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md)  
 [Najlepsze rozwiązania: przechowywanie wersji kontraktów danych](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md)
