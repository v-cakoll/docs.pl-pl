---
title: 103 - ActivityStateRecord
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 57636a9a-561e-44aa-aef9-1f1894aaa6dd
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 41621ccc634fec9212b84e88c089527b9e502648
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="103---activitystaterecord"></a>103 - ActivityStateRecord
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|103|  
|Słowa kluczowe|EndToEndMonitoring rozwiązywania problemów, HealthMonitoring, WFTracking|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows aplikacji Server aplikacje/analityczne|  
  
## <a name="description"></a>Opis  
 To zdarzenie jest emitowany przez uczestnika śledzenia zdarzeń systemu Windows podczas działania w ramach wystąpienia przepływu pracy emituje ActivityStateRecord  
  
## <a name="message"></a>Komunikat  
 TrackRecord = ActivityStateRecord, identyfikator wystąpienia = %1, RecordNumber = %2, EventTime = %3, stan = %4, Nazwa = %5, identyfikator = %6, ActivityInstanceId = %7 ActivityTypeName = %8, argumenty = %9, zmienne = % 10 adnotacje = % 11, ProfileName = % 12  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Identyfikator wystąpienia|xs:GUID|Identyfikator wystąpienia przepływu pracy|  
|RecordNumber|xs:Long|Numer sekwencyjny emitowany rekordu|  
|eventTime|xs: DateTime|Godzina w formacie UTC podczas zdarzenia zostały wyemitowane|  
|Stan|xs:String|Stan działania|  
|Nazwa|xs:String|Nazwa wyświetlana wysyłanego zdarzenia działania|  
|Identyfikator działania|xs:String|Identyfikator działania emisji działania|  
|ActivityInstanceId|xs:String|Identyfikator wystąpienia działania emisji działania|  
|ActivityTypeName|xs:String|Nazwa typu działania emisji|  
|Argumenty|xs:String|Argumenty, które są śledzone z tym zdarzeniem.  Wartości są przechowywane w elemencie xml w formacie \<elementy >\< nazwa elementu = "argumentName" type="System.String" > argumentValue\</elementu > \< /elementy >.  Jeśli zostały śledzone bez argumentów, a następnie ciąg zawiera \<elementów / >. Rozmiar zdarzenia ETW jest ograniczona przez rozmiar bufora ETW lub max ładunku zdarzenia ETW. Jeśli limity ETW przekracza rozmiar zdarzenia, a następnie zdarzenia został obcięty przez usunięcie adnotacje i zastąpienie wartości adnotacji z \<elementy >...  \< /elementy >.  Następujące typy są przechowywane jako wartości zwracane przez ToString(); String,char,bool,int,short,Long,uint,ushort,ulong,system.Single,float,Double,system.GUID,system.DateTimeOffset,system.DateTime.  Wszystkie inne typy są serializowane, przy użyciu System.Runtime.Serialization.NetDataContractSerializer.|  
|Zmienne|xs:String|Zmienne, które są śledzone z tym zdarzeniem.  Wartości są przechowywane w elemencie xml w formacie \<elementy >\< nazwa elementu = "nazwa_zmiennej" type="System.String" > variableValue\</elementu > \< /elementy >.  Jeśli zostały śledzone żadnych zmiennych, ciąg zawiera \<elementów / >. Rozmiar zdarzenia ETW jest ograniczona przez rozmiar bufora ETW lub max ładunku zdarzenia ETW. Jeśli limity ETW przekracza rozmiar zdarzenia, a następnie zdarzenia został obcięty przez usunięcie adnotacje i zastąpienie wartości zmiennych z \<elementy >...  \< /elementy >.  Następujące typy są przechowywane jako wartości zwracane przez ToString(); String,char,bool,int,short,Long,uint,ushort,ulong,system.Single,float,Double,system.GUID,system.DateTimeOffset,system.DateTime.  Wszystkie inne typy są serializowane, przy użyciu System.Runtime.Serialization.NetDataContractSerializer.|  
|Adnotacje|xs:String|Adnotacje, które zostały dodane do tego zdarzenia.  Wartości są przechowywane w elemencie xml w formacie \<elementy >\< nazwa elementu = "annotationName" type="System.String" > annotationValue\</elementu > \< /elementy >.  Jeśli nie określono bez adnotacji, a następnie ciąg zawiera \<elementów / >. Rozmiar zdarzenia ETW jest ograniczona przez rozmiar bufora ETW lub max ładunku zdarzenia ETW. Jeśli limity ETW przekracza rozmiar zdarzenia, a następnie zdarzenia został obcięty przez usunięcie adnotacje i zastąpienie wartości adnotacji z \<elementy >...  \< /elementy >.|  
|ProfileName|xs:String|Nazwa lub profilu śledzenia, które spowodowały to zdarzenie jest emitowany|  
|HostReference|xs:String|Dla usług sieci web hostowanych w tym polu unikatowo identyfikuje usługę w hierarchii sieci web.  Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web &#124; Ścieżka wirtualna usługi &#124; ServiceName "przykład:" Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService "|  
|Domeny aplikacji|xs:String|Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.|
