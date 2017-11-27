---
title: TcpTransportBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 33bbc1e5-44e4-4ee3-b7b5-801dc78956e4
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 180e954661319cb32edfd3180418fe9b1571ea5c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="tcptransportbindingelement"></a>TcpTransportBindingElement
TcpTransportBindingElement  
  
## <a name="syntax"></a>Składnia  
  
```  
class TcpTransportBindingElement : ConnectionOrientedTransportBindingElement  
{  
  TcpConnectionPoolSettings ConnectionPoolSettings;  
  sint32 ListenBacklog;  
  boolean PortSharingEnabled;  
  boolean TeredoEnabled;  
};  
```  
  
## <a name="methods"></a>Metody  
 Klasa TcpTransportBindingElement nie definiuje żadnych metod.  
  
## <a name="properties"></a>Właściwości  
 Klasa TcpTransportBindingElement ma następujące właściwości:  
  
### <a name="connectionpoolsettings"></a>ConnectionPoolSettings  
 Typ danych: TcpConnectionPoolSettings  
  
 Dostęp typu: tylko do odczytu  
  
 Ustawienia puli połączeń.  
  
### <a name="listenbacklog"></a>ListenBacklog  
 Typ danych: sint32  
  
 Dostęp typu: tylko do odczytu  
  
 Maksymalna liczba oczekujących żądań połączenia w kolejce.  
  
### <a name="portsharingenabled"></a>PortSharingEnabled  
 Typ danych: wartość logiczna  
  
 Dostęp typu: tylko do odczytu  
  
 Wartość logiczna określająca, czy włączone jest udostępnianie portów TCP dla tego połączenia.  
  
### <a name="teredoenabled"></a>TeredoEnabled  
 Typ danych: wartość logiczna  
  
 Dostęp typu: tylko do odczytu  
  
 Wartość logiczna określająca czy włączona jest obsługa technologii Teredo (pozwalającej adresować klientów znajdujących się za zaporą).  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowany w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowany w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>
