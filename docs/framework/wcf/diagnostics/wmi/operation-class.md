---
title: Operation — klasa
ms.date: 03/30/2017
ms.assetid: b19d1496-ef06-4d0c-b2ae-e728ec00cca0
ms.openlocfilehash: 9696a7f026e54afacb5ccbfa8703a2ba617a9f3d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59165083"
---
# <a name="operation-class"></a>Operation — klasa
Operacja  
  
## <a name="syntax"></a>Składnia  
  
```csharp
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
 Klasa Operation nie definiuje żadnych metod.  
  
## <a name="properties"></a>Właściwości  
 Klasa Operation ma następujące właściwości:  
  
### <a name="action"></a>Akcja  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Akcja WS-Addressing komunikatu żądania.  
  
### <a name="asyncpattern"></a>AsyncPattern  
 Typ danych: wartość logiczna  
  
 Typ dostępu: tylko do odczytu  
  
 Wskazuje, że operacja jest wykonywane asynchronicznie za pomocą `Begin`[/ zamykającego nawiasy kątowe] i `End`pary — metoda [nawiasy otwarte i zamknięte] w kontrakcie usługi.  
  
### <a name="behaviors"></a>Zachowania  
 Typ danych: Zachowanie tablicy  
  
 Typ dostępu: tylko do odczytu  
  
 Zachowania skojarzone z tą operacją.  
  
### <a name="iscallback"></a>IsCallback  
 Typ danych: wartość logiczna  
  
 Typ dostępu: tylko do odczytu  
  
 Wartość true, gdy operacja jest operacji wywołania zwrotnego.  
  
### <a name="isinitiating"></a>IsInitiating  
 Typ danych: wartość logiczna  
  
 Typ dostępu: tylko do odczytu  
  
 Wskazuje, czy metoda implementuje operację, która może zainicjować sesję na serwerze.  
  
### <a name="isoneway"></a>IsOneWay  
 Typ danych: wartość logiczna  
  
 Typ dostępu: tylko do odczytu  
  
 Wskazuje, czy operacja zwraca komunikat odpowiedzi.  
  
### <a name="isterminating"></a>IsTerminating  
 Typ danych: wartość logiczna  
  
 Typ dostępu: tylko do odczytu  
  
 Wskazuje, czy operacja zwraca komunikat odpowiedzi.  
  
### <a name="methodsignature"></a>MethodSignature  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Podpis metody operacji.  
  
### <a name="name"></a>Nazwa  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Nazwa operacji.  
  
### <a name="parametertypes"></a>ParameterTypes  
 Typ danych: tablica ciągów  
  
 Typ dostępu: tylko do odczytu  
  
 Typy parametrów operacji.  
  
### <a name="replyaction"></a>Parametr ReplyAction  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Wartość Akcja SOAP komunikat odpowiedzi operacji.  
  
### <a name="returntype"></a>ReturnType  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Zwracany typ operacji.  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowana w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowane w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Description.OperationDescription>
