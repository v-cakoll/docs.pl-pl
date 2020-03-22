---
title: Operacje związane z portem w oprogramowaniu .NET Framework
ms.date: 07/20/2015
helpviewer_keywords:
- ports, Visual Basic
ms.assetid: 1eba223b-7bd3-401a-b097-982bce96df1b
ms.openlocfilehash: 68f0c67b8135c6bb7ce8a134e2a324bc12c0aad9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345504"
---
# <a name="port-operations-in-the-net-framework-with-visual-basic"></a>Operacje związane z portem w oprogramowaniu .NET Framework przeprowadzane za pomocą Visual Basic

Dostęp do portów szeregowych komputera można uzyskać za <xref:System.IO.Ports?displayProperty=nameWithType> pośrednictwem klas .NET Framework w obszarze nazw. Najważniejsza klasa <xref:System.IO.Ports.SerialPort>, zapewnia ramy dla synchronicznych i opartych na zdarzeniach we/wy, dostęp do stanów przypięcia i przerwania oraz dostęp do właściwości sterownika szeregowego. Może być zawinięty <xref:System.IO.Stream> w obiekt, <xref:System.IO.Ports.SerialPort.BaseStream> dostępny za pośrednictwem właściwości. <xref:System.IO.Ports.SerialPort> Zawijanie <xref:System.IO.Stream> w obiekcie umożliwia dostęp do portu szeregowego przez klasy, które używają strumieni. Obszar nazw zawiera wyliczenia, które upraszczają kontrolę nad portami szeregowymi.

Najprostszym sposobem utworzenia <xref:System.IO.Ports.SerialPort> obiektu jest <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A> za pomocą metody.

> [!NOTE]
> Nie można używać klas programu .NET Framework do bezpośredniego dostępu do innych typów portów, takich jak porty równoległe, porty USB i tak dalej.

## <a name="enumerations"></a>Wyliczenia

W tej tabeli wymieniono i opisano główne wyliczenia używane do uzyskiwania dostępu do portu szeregowego:

|Wyliczenie|Opis|
|---|---|
|<xref:System.IO.Ports.Handshake>|Określa protokół sterowania używany do ustanawiania komunikacji <xref:System.IO.Ports.SerialPort> portu szeregowego dla obiektu.|
|<xref:System.IO.Ports.Parity>|Określa bit parzystości <xref:System.IO.Ports.SerialPort> dla obiektu.|
|<xref:System.IO.Ports.SerialData>|Określa typ znaku odebranego na porcie szeregowym <xref:System.IO.Ports.SerialPort> obiektu.|
|<xref:System.IO.Ports.SerialError>|Określa błędy występujące w <xref:System.IO.Ports.SerialPort> obiekcie|
|<xref:System.IO.Ports.SerialPinChange>|Określa typ zmiany, która wystąpiła <xref:System.IO.Ports.SerialPort> w obiekcie.|
|<xref:System.IO.Ports.StopBits>|Określa liczbę bitów zatrzymania używanych <xref:System.IO.Ports.SerialPort> w obiekcie.|

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.Devices.Ports>
- [Uzyskiwanie dostępu do portów komputera](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-computer-s-ports.md)
