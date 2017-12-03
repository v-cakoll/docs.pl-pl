---
title: Binding2
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 09511c6c-5749-4bb0-874e-0f0be36bfe04
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b9e44d161e1229db9145f4ed7e337396bbd98c68
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="binding"></a>Powiązanie
WMI powiązania  
  
## <a name="syntax"></a>Składnia  
  
```  
class Binding  
{  
  BindingElement BindingElements[];  
  datetime CloseTimeout;  
  string Name;  
  string Namespace;  
  datetime OpenTimeout;  
  datetime ReceiveTimeout;  
  string Scheme;  
  datetime SendTimeout;  
};  
```  
  
## <a name="methods"></a>Metody  
 Klasa powiązania nie definiuje żadnych metod.  
  
## <a name="properties"></a>Właściwości  
 Klasa powiązania ma następujące właściwości.  
  
### <a name="bindingelements"></a>Elementy BindingElements  
 Typ danych: tablica BindingElement  
  
 Dostęp typu: tylko do odczytu  
  
 Kolekcja elementów powiązań implementowanych przez powiązanie.  
  
### <a name="closetimeout"></a>closeTimeout  
 Typ danych: daty i godziny  
  
 Dostęp typu: tylko do odczytu  
  
 Interwał przeznaczony na zakończenie operacji zamknięcia.  
  
### <a name="name"></a>Nazwa  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Nazwa powiązania.  
  
### <a name="namespace"></a>Przestrzeń nazw  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Przestrzeń nazw XML powiązania.  
  
### <a name="opentimeout"></a>openTimeout  
 Typ danych: daty i godziny  
  
 Dostęp typu: tylko do odczytu  
  
 Interwał przeznaczony na zakończenie operacji otwarcia.  
  
### <a name="receivetimeout"></a>receiveTimeout  
 Typ danych: daty i godziny  
  
 Dostęp typu: tylko do odczytu  
  
 Interwał przeznaczony na zakończenie operacji odbioru.  
  
### <a name="scheme"></a>Schemat  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Schemat transportu identyfikatora URI, który jest używany przez fabryki kanału i odbiornika zbudowane na podstawie powiązania.  
  
### <a name="sendtimeout"></a>właściwości sendTimeout  
 Typ danych: daty i godziny  
  
 Dostęp typu: tylko do odczytu  
  
 Interwał przeznaczony na zakończenie operacji wysyłania.  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowany w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowany w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Channels.Binding>
