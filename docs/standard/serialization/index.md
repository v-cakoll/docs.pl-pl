---
title: Serializacja w .NET
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- XML serialization, defined
- binary serialization
- serializing objects
- serialization
- objects, serializing
ms.assetid: 4d1111c0-9447-4231-a997-96a2b74b3453
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 1a0d9f5fd32b5610e3d7b05455c7bd3c55b5b77e
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="serialization-in-net"></a>Serializacja w .NET
Serializacja jest proces konwersji stan obiektu do formularza, które mogą być utrwalone lub transportowane. Uzupełnienie serializacji jest deserializacji, które służy do obiektu strumienia. Razem te procesy umożliwiają danych można łatwo przechowywane i przekazywane.  
  
Usług .NET features dwie technologie serializacji:  
  
-   Serializacja binarna zachowuje wierności typów, co jest przydatne, aby zachować stan obiektu między różnymi wywołaniami aplikacji. Na przykład można udostępniać obiekt między różnymi aplikacjami, szeregując go do Schowka. Można serializować obiektu w strumieniu na dysku w pamięci, za pośrednictwem sieci i tak dalej. Komunikację zdalną używa serializacji do przekazania obiektów "przez wartość" z jednej domeny komputera lub aplikacji na inny.  
  
-   Serializacji XML serializuje tylko właściwości publiczne i pola i nie zostaną zachowane wierności typu. Jest to przydatne, jeśli chcesz dostarczyć lub użyć danych bez ograniczania aplikacji korzystającej z danych. Ponieważ kod XML jest otwarty standard, jest atrakcyjny wybór udostępnianie danych w sieci Web. Podobnie protokołu SOAP jest otwarty standard, co pozwala na wybór atrakcyjny.  
  
## <a name="in-this-section"></a>W tej sekcji  
[Serializacja — instrukcje](../../../docs/standard/serialization/serialization-how-to-topics.md)  
Zawiera także łącza do tematów instrukcje zawarte w tej sekcji.
  
[Serializacja binarna](../../../docs/standard/serialization/binary-serialization.md)  
Opisuje mechanizm serializacji binarnej, który jest dołączony do aparatu PLików wykonywalnych języka wspólnego.

[Serializacja XML i SOAP](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
Opisuje mechanizm serializacji XML i protokołu SOAP, który jest dołączony do aparatu PLików wykonywalnych języka wspólnego.

[Narzędzia do serializacji](../../../docs/standard/serialization/serialization-tools.md)  
Te narzędzia ułatwiają tworzenie kodu serializacji.

[Przykłady serializacji](../../../docs/standard/serialization/serialization-samples.md)  
Przykłady pokazują, jak to zrobić serializacji.

## <a name="reference"></a>Tematy pomocy
<xref:System.Runtime.Serialization>Zawiera klasy, które mogą służyć do serializacji i deserializacji obiektów.
  
<xref:System.Xml.Serialization>  
Zawiera klasy, których można użyć do wykonywania serializacji obiektów w dokumentach formatu XML lub strumieni.