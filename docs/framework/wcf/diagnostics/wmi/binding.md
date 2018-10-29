---
title: Binding2
ms.date: 03/30/2017
ms.assetid: 09511c6c-5749-4bb0-874e-0f0be36bfe04
ms.openlocfilehash: 84e304f3dedcbd785d6238e6cb5eb142c288b995
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2018
ms.locfileid: "50198892"
---
# <a name="binding"></a>Powiązanie
WMI powiązania  
  
## <a name="syntax"></a>Składnia  
  
```csharp
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
  
 Dostęp do typu: tylko do odczytu  
  
 Kolekcja elementów powiązań implementowanych przez powiązanie.  
  
### <a name="closetimeout"></a>closeTimeout  
 Typ danych: Data i godzina  
  
 Dostęp do typu: tylko do odczytu  
  
 Przedział czasu przewidzianego na zakończenie operacji zamknięcia.  
  
### <a name="name"></a>Nazwa  
 Typ danych: ciąg  
  
 Dostęp do typu: tylko do odczytu  
  
 Nazwa powiązania.  
  
### <a name="namespace"></a>Przestrzeń nazw  
 Typ danych: ciąg  
  
 Dostęp do typu: tylko do odczytu  
  
 Przestrzeń nazw XML powiązania.  
  
### <a name="opentimeout"></a>OpenTimeout  
 Typ danych: Data i godzina  
  
 Dostęp do typu: tylko do odczytu  
  
 Przedział czasu przewidzianego na zakończenie operacji Otwórz.  
  
### <a name="receivetimeout"></a>ReceiveTimeout  
 Typ danych: Data i godzina  
  
 Dostęp do typu: tylko do odczytu  
  
 Przedział czasu przewidzianego na ukończenie operacji odbierania.  
  
### <a name="scheme"></a>Schemat  
 Typ danych: ciąg  
  
 Dostęp do typu: tylko do odczytu  
  
 Schemat transportu identyfikatora URI jest używany przez fabryki kanału i odbiornika, które są tworzone przez wiązanie.  
  
### <a name="sendtimeout"></a>Właściwości SendTimeout  
 Typ danych: Data i godzina  
  
 Dostęp do typu: tylko do odczytu  
  
 Przedział czasu przewidzianego na ukończenie operacji wysyłania.  
  
## <a name="requirements"></a>Wymagania  
  
|PLIK MOF|Zadeklarowana w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowane w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Channels.Binding>
