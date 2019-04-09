---
title: MustUnderstandBehavior
ms.date: 03/30/2017
ms.assetid: 911ed04a-c4b8-4c72-a5c3-fc7b4e3b4348
ms.openlocfilehash: 7e6a96c217b038e870b4e865315766afa3b3c757
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59165479"
---
# <a name="mustunderstandbehavior"></a>MustUnderstandBehavior
MustUnderstandBehavior  
  
## <a name="syntax"></a>Składnia  
  
```csharp
class MustUnderstandBehavior : Behavior  
{  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a>Metody  
 Klasa MustUnderstandBehavior nie definiuje żadnych metod.  
  
## <a name="properties"></a>Właściwości  
 Klasa MustUnderstandBehavior ma następującą właściwość:  
  
### <a name="validatemustunderstand"></a>ValidateMustUnderstand  
 Typ danych: wartość logiczna  
  
 Typ dostępu: tylko do odczytu  
  
 Gdy `true`, wszystkich nagłówków protokołu SOAP z `MustUnderstand` atrybutów, które nie są obsługiwane, że zachowanie, aby zgłosić wyjątek.  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowana w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowane w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Description.MustUnderstandBehavior>
