---
title: Transport integracji usługi MSMQ
ms.date: 03/30/2017
ms.assetid: 2bf9893a-fbd1-41fc-b6de-a41a44279936
ms.openlocfilehash: 52fd98354ded57bd7d7c075d4f08ca543760e598
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777367"
---
# <a name="msmq-integration-transport"></a>Transport integracji usługi MSMQ
Ten temat zawiera listę wszystkich wyjątków generowanych przez Transport integracji usługi MSMQ.  
  
## <a name="exception-list"></a>Lista wyjątków  
  
|Kod zasobu|Ciąg zasobu|  
|-------------------|---------------------|  
|MessageSizeMustBeInIntegerRange|Ta fabryka buforuje wiadomości, więc rozmiary wiadomości muszą być z zakresu liczb całkowitych.|  
|MsmqByteArrayBodyExpected|Wystąpiła niezgodność między format serializacji określonego i treści wiadomości usługi MSMQ. Komunikat nie mogą być wysyłane lub odbierane. Format serializacji ByteArray wymaga treści wiadomości usługi MSMQ jako typu byte [].|  
|MsmqCannotDeserializeActiveXMessage|Wystąpił błąd serializacji ActiveX. Komunikat nie mogą być wysyłane lub odbierane. Określony typ wariantu dla treści jest niezgodna z rzeczywista treść wiadomości usługi MSMQ.|  
|MsmqCannotUseBodyTypeWithActiveXSerialization|Właściwości wiadomości są niezgodne. Komunikat nie mogą być wysyłane lub odbierane. Właściwości wiadomości BodyType nie może być określona, jeśli jest używany format serializacji ActiveX.|  
|MsmqInvalidServiceOperationForMsmqIntegrationBinding|Nie można zweryfikować MsmqIntegrationBinding. Nie można uruchomić punktu końcowego usługi. Określone powiązanie nie obsługuje podpis metody dla operacji określonej usługi w określonym kontraktu. Popraw operacji usługi przy użyciu MsmqIntegrationBinding.|  
|MsmqInvalidTypeDeserialization|Serializacja ActiveX nie powiodła się, ponieważ nie można rozpoznać formatu serializacji. Komunikat nie mogą być wysyłane lub odbierane.|  
|MsmqInvalidTypeSerialization|Nie rozpoznano typu variant. Serializacja ActiveX nie powiodła się. Komunikat nie mogą być wysyłane lub odbierane. Określony typ wariantu nie jest obsługiwany.|  
|MsmqStreamBodyExpected|Niezgodność między formatem serializacji i zawartości. Komunikat nie mogą być wysyłane lub odbierane. Treść strumienia typu mogą być wysyłane lub odebranych przy użyciu strumienia tryb serializacji.|
