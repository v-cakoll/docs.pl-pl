---
title: Operacje związane z portem w oprogramowaniu .NET Framework
ms.date: 07/20/2015
helpviewer_keywords:
- ports, Visual Basic
ms.assetid: 1eba223b-7bd3-401a-b097-982bce96df1b
ms.openlocfilehash: 0ef0b8a7aec40603185d227d972cea655fd238c1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84360140"
---
# <a name="port-operations-in-the-net-framework-with-visual-basic"></a>Operacje związane z portem w oprogramowaniu .NET Framework przeprowadzane za pomocą Visual Basic

Dostęp do portów szeregowych komputera można uzyskać za pomocą klas .NET Framework w <xref:System.IO.Ports?displayProperty=nameWithType> przestrzeni nazw. Najważniejszym klasą, <xref:System.IO.Ports.SerialPort> ,, jest struktura synchronicznych i opartych na zdarzeniach operacji we/wy, dostęp do numerów PIN i stan przerwania oraz dostęp do właściwości sterownika szeregowego. Może być opakowany w <xref:System.IO.Stream> obiekt, dostępny za pomocą <xref:System.IO.Ports.SerialPort.BaseStream> właściwości. Zawijanie <xref:System.IO.Ports.SerialPort> w <xref:System.IO.Stream> obiekcie umożliwia dostęp do portu szeregowego przez klasy, które używają strumieni. Przestrzeń nazw zawiera wyliczenia, które upraszczają kontrolę portów szeregowych.

Najprostszym sposobem utworzenia <xref:System.IO.Ports.SerialPort> obiektu jest użycie <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A> metody.

> [!NOTE]
> Nie można użyć .NET Framework klas do bezpośredniego dostępu do innych typów portów, takich jak porty równoległe, porty USB i tak dalej.

## <a name="enumerations"></a>Wyliczenia

W tej tabeli wymieniono główne wyliczenia używane do uzyskiwania dostępu do portu szeregowego:

|Wyliczenie|Opis|
|---|---|
|<xref:System.IO.Ports.Handshake>|Określa protokół kontroli używany do ustanawiania komunikacji portu szeregowego dla <xref:System.IO.Ports.SerialPort> obiektu.|
|<xref:System.IO.Ports.Parity>|Określa bit parzystości dla <xref:System.IO.Ports.SerialPort> obiektu.|
|<xref:System.IO.Ports.SerialData>|Określa typ znaku, który został odebrany przez port szeregowy <xref:System.IO.Ports.SerialPort> obiektu.|
|<xref:System.IO.Ports.SerialError>|Określa błędy występujące w <xref:System.IO.Ports.SerialPort> obiekcie|
|<xref:System.IO.Ports.SerialPinChange>|Określa typ zmiany, która wystąpiła w <xref:System.IO.Ports.SerialPort> obiekcie.|
|<xref:System.IO.Ports.StopBits>|Określa liczbę bitów stopu używanych w <xref:System.IO.Ports.SerialPort> obiekcie.|

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.Devices.Ports>
- [Uzyskiwanie dostępu do portów komputera](accessing-the-computer-s-ports.md)
