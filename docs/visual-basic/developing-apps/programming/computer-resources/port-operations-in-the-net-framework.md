---
title: Operacje związane z portem w oprogramowaniu .NET Framework przeprowadzane za pomocą Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- ports, Visual Basic
ms.assetid: 1eba223b-7bd3-401a-b097-982bce96df1b
ms.openlocfilehash: e9927df7b646da6c66c11a5a686c4b038aaea774
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591370"
---
# <a name="port-operations-in-the-net-framework-with-visual-basic"></a>Operacje związane z portem w oprogramowaniu .NET Framework przeprowadzane za pomocą Visual Basic
Dostęp do portów szeregowych na komputerze przy użyciu klas .NET Framework w <xref:System.IO.Ports?displayProperty=nameWithType> przestrzeni nazw. Najważniejsze klasy <xref:System.IO.Ports.SerialPort>, zapewnia ramy pozwalające synchroniczne i oparte na zdarzeniach operacji We/Wy, dostępu stanom pin i podziału i dostęp do właściwości sterownika szeregowe. Mogą być ujęte w <xref:System.IO.Stream> obiekt, za pośrednictwem <xref:System.IO.Ports.SerialPort.BaseStream> właściwości. Zawijanie <xref:System.IO.Ports.SerialPort> w <xref:System.IO.Stream> obiekt umożliwia portu szeregowego dostępu do klasy, które używają strumieni. Przestrzeń nazw zawiera wyliczenia, które ułatwiają kontrolę nad portów szeregowych.  
  
 Najprostszym sposobem utworzenia <xref:System.IO.Ports.SerialPort> obiekt jest za pośrednictwem <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A> metody.  
  
> [!NOTE]
>  Nie można użyć klas .NET Framework w celu uzyskania bezpośredniego dostępu do innych typów porty, na przykład portów równoległych, portów USB i tak dalej.  
  
## <a name="enumerations"></a>Wyliczenia  
 W tej tabeli wymieniono i opisano główne wyliczenia używane do uzyskiwania dostępu do portu szeregowego:  
  
|Wyliczenie|Opis|  
|---|---|   
|<xref:System.IO.Ports.Handshake>|Określa protokół kontroli używany podczas ustanawiania port szeregowy komunikacji dla <xref:System.IO.Ports.SerialPort> obiektu.|  
|<xref:System.IO.Ports.Parity>|Określa bitu parzystości do <xref:System.IO.Ports.SerialPort> obiektu.|  
|<xref:System.IO.Ports.SerialData>|Określa typ znaku, który został odebrany przez port szeregowy z <xref:System.IO.Ports.SerialPort> obiektu.|  
|<xref:System.IO.Ports.SerialError>|Określa błędów występujących na <xref:System.IO.Ports.SerialPort> obiektu|  
|<xref:System.IO.Ports.SerialPinChange>|Określa typ zmiany, która wystąpiła w <xref:System.IO.Ports.SerialPort> obiektu.|  
|<xref:System.IO.Ports.StopBits>|Określa liczbę bitów stop na <xref:System.IO.Ports.SerialPort> obiektu.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.Devices.Ports>
- [Uzyskiwanie dostępu do portów komputera](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-computer-s-ports.md)
