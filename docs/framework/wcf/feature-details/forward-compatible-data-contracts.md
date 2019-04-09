---
title: Kontrakty danych zgodne z nowszymi wersjami
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], forward compatibility
ms.assetid: 413c9044-26f8-4ecb-968c-18495ea52cd9
ms.openlocfilehash: 90d9409d7e41ddda99caf24ebe0e249ee04723d6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59095896"
---
# <a name="forward-compatible-data-contracts"></a>Kontrakty danych zgodne z nowszymi wersjami
Funkcji programu Windows Communication Foundation (WCF) to system kontraktu danych, kontraktów może z czasem ewoluować względami nieprzerywającymi działania aplikacji. Oznacza to, że klienta ze starszą wersją kontraktu danych może komunikować się z usługą za pomocą nowszej wersji tego samego kontraktu danych lub klienta za pomocą nowszej wersji kontraktu danych może komunikować się ze starszą wersją tej samej umowy dotyczącej danych. Aby uzyskać więcej informacji, zobacz [najlepsze rozwiązania: Przechowywanie wersji kontraktów danych](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md).  
  
 Większość funkcji przechowywania wersji można stosować na zgodnie z potrzebami, podczas tworzenia nowych wersji istniejących kontraktu danych. Jednak jedna z funkcji przechowywania wersji, *Pełna zgodnooć wersji*, muszą zostać skompilowane do typu z pierwszej wersji, aby zapewnić prawidłowe działanie.  
  
## <a name="round-tripping"></a>Pełna zgodnooć wersji  
 Pełna zgodnooć wersji występuje, gdy dane są przesyłane z nową wersję do starszej wersji i powrót do nowej wersji kontraktu danych. Pełna zgodnooć wersji gwarantuje, że żadne dane nie zostaną utracone. Włączanie Pełna zgodnooć wersji sprawia, że typ zgodne ze wszystkimi zmianami przyszłych obsługiwane przez model versioning kontraktu danych.  
  
 Aby włączyć Pełna zgodnooć wersji dla określonego typu, musi implementować typ <xref:System.Runtime.Serialization.IExtensibleDataObject> interfejsu. Interfejs zawiera jedną właściwość <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> (zwracanie <xref:System.Runtime.Serialization.ExtensionDataObject> typu). Właściwość przechowuje wszystkie dane z przyszłych wersji kontraktu danych, który jest nieznany do bieżącej wersji.  
  
### <a name="example"></a>Przykład  
 Następujące kontraktu danych nie jest zgodne ze zmianami w przyszłości.  
  
 [!code-csharp[C_DataContract#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#7)]
 [!code-vb[C_DataContract#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#7)]  
  
 Aby typ zgodny z przyszłe zmiany (na przykład dodając nowy element członkowski danych o nazwie "phoneNumber"), należy zaimplementować <xref:System.Runtime.Serialization.IExtensibleDataObject> interfejsu.  
  
 [!code-csharp[C_DataContract#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#8)]
 [!code-vb[C_DataContract#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#8)]  
  
 Jeśli infrastruktura WCF napotka dane, które nie są częścią oryginalnej kontraktu danych, dane są przechowywane we właściwości i zachowane. Nie jest wykonywane w jakikolwiek inny sposób, z wyjątkiem magazynu tymczasowego. Jeśli obiekt jest zwracany, do którego pochodzi, zwracany jest również oryginalnych danych (nieznany). W związku z tym dane podejścia biznesowego uczyniło rund do i z źródłowy punkt końcowy bez utraty. Należy jednak pamiętać, że w razie potrzeby dane do przetworzenia źródłowy punkt końcowy tego oczekiwania jest niewypełnienia, a punkt końcowy musi jakiś sposób wykrywania i wprowadzać zmiany.  
  
 <xref:System.Runtime.Serialization.ExtensionDataObject> Typ nie zawiera żadnych metod ani właściwości. W związku z tym, nie można uzyskać bezpośredni dostęp do danych przechowywanych w <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> właściwości.  
  
 Funkcja Pełna zgodnooć wersji może zostać wyłączony, albo ustawiając `ignoreExtensionDataObject` do `true` w <xref:System.Runtime.Serialization.DataContractSerializer> konstruktora lub przez ustawienie <xref:System.ServiceModel.ServiceBehaviorAttribute.IgnoreExtensionDataObject%2A> właściwości `true` na <xref:System.ServiceModel.ServiceBehaviorAttribute>. Gdy ta funkcja jest wyłączona, Deserializator nie zostanie wypełniony <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> właściwość i Serializator nie Emituj zawartość właściwości.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.Serialization.IExtensibleDataObject>
- <xref:System.Runtime.Serialization.ExtensionDataObject>
- [Przechowywanie wersji kontraktów danych](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md)
- [Najlepsze rozwiązania: Przechowywanie wersji kontraktów danych](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md)
