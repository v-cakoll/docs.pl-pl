---
title: "Operation — klasa"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b19d1496-ef06-4d0c-b2ae-e728ec00cca0
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 739f8309e7a01eeecf921b50fcde24417fbbc515
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="operation-class"></a>Operation — klasa
Operacja  
  
## <a name="syntax"></a>Składnia  
  
```  
class Operation  
{  
  string Action;  
  boolean AsyncPattern;  
  Behavior Behaviors[];  
  boolean IsCallback;  
  boolean IsInitiating;  
  boolean IsOneWay;  
  boolean IsTerminating;  
  string MethodSignature;  
  string Name;  
  string ParameterTypes[];  
  string ReplyAction;  
  string ReturnType;  
};  
```  
  
## <a name="methods"></a>Metody  
 Klasa operacji nie definiuje żadnych metod.  
  
## <a name="properties"></a>Właściwości  
 Klasa operacja ma następujące właściwości:  
  
### <a name="action"></a>Akcja  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Akcja WS-Addressing komunikatu żądania.  
  
### <a name="asyncpattern"></a>AsyncPattern  
 Typ danych: wartość logiczna  
  
 Dostęp typu: tylko do odczytu  
  
 Wskazuje, że operacja jest zaimplementowana asynchronicznie za pomocą `Begin`[otwierającego/zamykającego nawiasu ostrego] i `End`[otwierającego/zamykającego nawiasu ostrego] pary metod w kontrakcie usługi.  
  
### <a name="behaviors"></a>Zachowania  
 Typ danych: zachowanie tablicy  
  
 Dostęp typu: tylko do odczytu  
  
 Zachowania skojarzone z tą operacją.  
  
### <a name="iscallback"></a>IsCallback  
 Typ danych: wartość logiczna  
  
 Dostęp typu: tylko do odczytu  
  
 Wartość PRAWDA, jeśli operacja jest wywołaniem zwrotnym.  
  
### <a name="isinitiating"></a>IsInitiating  
 Typ danych: wartość logiczna  
  
 Dostęp typu: tylko do odczytu  
  
 Wskazuje, czy metoda implementuje operację umożliwiającą inicjację sesji na serwerze.  
  
### <a name="isoneway"></a>Ustawienie właściwości IsOneWay  
 Typ danych: wartość logiczna  
  
 Dostęp typu: tylko do odczytu  
  
 Wskazuje, czy operacja zwraca komunikat odpowiedzi.  
  
### <a name="isterminating"></a>IsTerminating  
 Typ danych: wartość logiczna  
  
 Dostęp typu: tylko do odczytu  
  
 Wskazuje, czy operacja zwraca komunikat odpowiedzi.  
  
### <a name="methodsignature"></a>MethodSignature  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Podpis metody operacji.  
  
### <a name="name"></a>Nazwa  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Nazwa operacji.  
  
### <a name="parametertypes"></a>ParameterTypes  
 Typ danych: tablicy ciągów  
  
 Dostęp typu: tylko do odczytu  
  
 Typy parametrów operacji.  
  
### <a name="replyaction"></a>Parametr ReplyAction  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Wartość akcji SOAP dla komunikatu odpowiedzi operacji.  
  
### <a name="returntype"></a>Obiekt ReturnType  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Zwracany typ operacji.  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowany w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowany w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Description.OperationDescription>
