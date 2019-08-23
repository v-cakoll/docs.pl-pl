---
title: Operacje związane z portem w oprogramowaniu .NET Framework przeprowadzane za pomocą Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- ports, Visual Basic
ms.assetid: 1eba223b-7bd3-401a-b097-982bce96df1b
ms.openlocfilehash: 936ff4c861444d3a971b38fd7b2a0af38b19494b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916604"
---
# <a name="port-operations-in-the-net-framework-with-visual-basic"></a>Operacje związane z portem w oprogramowaniu .NET Framework przeprowadzane za pomocą Visual Basic
Dostęp do portów szeregowych komputera można uzyskać za pomocą klas .NET Framework w <xref:System.IO.Ports?displayProperty=nameWithType> przestrzeni nazw. Najważniejszym klasą <xref:System.IO.Ports.SerialPort>,,, jest struktura synchronicznych i opartych na zdarzeniach operacji we/wy, dostęp do numerów PIN i stan przerwania oraz dostęp do właściwości sterownika szeregowego. Może być opakowany w <xref:System.IO.Stream> obiekt, dostępny <xref:System.IO.Ports.SerialPort.BaseStream> za pomocą właściwości. <xref:System.IO.Ports.SerialPort> Zawijanie<xref:System.IO.Stream> w obiekcie umożliwia dostęp do portu szeregowego przez klasy, które używają strumieni. Przestrzeń nazw zawiera wyliczenia, które upraszczają kontrolę portów szeregowych.  
  
 Najprostszym sposobem utworzenia <xref:System.IO.Ports.SerialPort> obiektu jest <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A> użycie metody.  
  
> [!NOTE]
> Nie można użyć .NET Framework klas do bezpośredniego dostępu do innych typów portów, takich jak porty równoległe, porty USB i tak dalej.  
  
## <a name="enumerations"></a>Wyliczenia  
 W tej tabeli wymieniono główne wyliczenia używane do uzyskiwania dostępu do portu szeregowego:  
  
|Wyliczenie|Opis|  
|---|---|   
|<xref:System.IO.Ports.Handshake>|Określa protokół kontroli używany do ustanawiania komunikacji portu szeregowego dla <xref:System.IO.Ports.SerialPort> obiektu.|  
|<xref:System.IO.Ports.Parity>|Określa bit parzystości dla <xref:System.IO.Ports.SerialPort> obiektu.|  
|<xref:System.IO.Ports.SerialData>|Określa typ znaku, który został odebrany przez port <xref:System.IO.Ports.SerialPort> szeregowy obiektu.|  
|<xref:System.IO.Ports.SerialError>|Określa błędy występujące w <xref:System.IO.Ports.SerialPort> obiekcie|  
|<xref:System.IO.Ports.SerialPinChange>|Określa typ zmiany, która wystąpiła w <xref:System.IO.Ports.SerialPort> obiekcie.|  
|<xref:System.IO.Ports.StopBits>|Określa liczbę bitów stopu używanych w <xref:System.IO.Ports.SerialPort> obiekcie.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.Devices.Ports>
- [Uzyskiwanie dostępu do portów komputera](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-computer-s-ports.md)
