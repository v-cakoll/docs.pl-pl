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
# <a name="port-operations-in-the-net-framework-with-visual-basic"></a><span data-ttu-id="3ada6-102">Operacje związane z portem w oprogramowaniu .NET Framework przeprowadzane za pomocą Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3ada6-102">Port Operations in the .NET Framework with Visual Basic</span></span>

<span data-ttu-id="3ada6-103">Dostęp do portów szeregowych komputera można uzyskać za pomocą klas .NET Framework w <xref:System.IO.Ports?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="3ada6-103">You can access your computer's serial ports through the .NET Framework classes in the <xref:System.IO.Ports?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="3ada6-104">Najważniejszym klasą, <xref:System.IO.Ports.SerialPort> ,, jest struktura synchronicznych i opartych na zdarzeniach operacji we/wy, dostęp do numerów PIN i stan przerwania oraz dostęp do właściwości sterownika szeregowego.</span><span class="sxs-lookup"><span data-stu-id="3ada6-104">The most important class, <xref:System.IO.Ports.SerialPort>, provides a framework for synchronous and event-driven I/O, access to pin and break states, and access to serial driver properties.</span></span> <span data-ttu-id="3ada6-105">Może być opakowany w <xref:System.IO.Stream> obiekt, dostępny za pomocą <xref:System.IO.Ports.SerialPort.BaseStream> właściwości.</span><span class="sxs-lookup"><span data-stu-id="3ada6-105">It can be wrapped in a <xref:System.IO.Stream> object, accessible through the <xref:System.IO.Ports.SerialPort.BaseStream> property.</span></span> <span data-ttu-id="3ada6-106">Zawijanie <xref:System.IO.Ports.SerialPort> w <xref:System.IO.Stream> obiekcie umożliwia dostęp do portu szeregowego przez klasy, które używają strumieni.</span><span class="sxs-lookup"><span data-stu-id="3ada6-106">Wrapping <xref:System.IO.Ports.SerialPort> in a <xref:System.IO.Stream> object allows the serial port to be accessed by classes that use streams.</span></span> <span data-ttu-id="3ada6-107">Przestrzeń nazw zawiera wyliczenia, które upraszczają kontrolę portów szeregowych.</span><span class="sxs-lookup"><span data-stu-id="3ada6-107">The namespace includes enumerations that simplify the control of serial ports.</span></span>

<span data-ttu-id="3ada6-108">Najprostszym sposobem utworzenia <xref:System.IO.Ports.SerialPort> obiektu jest użycie <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="3ada6-108">The simplest way to create a <xref:System.IO.Ports.SerialPort> object is through the <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A> method.</span></span>

> [!NOTE]
> <span data-ttu-id="3ada6-109">Nie można użyć .NET Framework klas do bezpośredniego dostępu do innych typów portów, takich jak porty równoległe, porty USB i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="3ada6-109">You cannot use .NET Framework classes to directly access other types of ports, such as parallel ports, USB ports, and so on.</span></span>

## <a name="enumerations"></a><span data-ttu-id="3ada6-110">Wyliczenia</span><span class="sxs-lookup"><span data-stu-id="3ada6-110">Enumerations</span></span>

<span data-ttu-id="3ada6-111">W tej tabeli wymieniono główne wyliczenia używane do uzyskiwania dostępu do portu szeregowego:</span><span class="sxs-lookup"><span data-stu-id="3ada6-111">This table lists and describes the main enumerations used for accessing a serial port:</span></span>

|<span data-ttu-id="3ada6-112">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="3ada6-112">Enumeration</span></span>|<span data-ttu-id="3ada6-113">Opis</span><span class="sxs-lookup"><span data-stu-id="3ada6-113">Description</span></span>|
|---|---|
|<xref:System.IO.Ports.Handshake>|<span data-ttu-id="3ada6-114">Określa protokół kontroli używany do ustanawiania komunikacji portu szeregowego dla <xref:System.IO.Ports.SerialPort> obiektu.</span><span class="sxs-lookup"><span data-stu-id="3ada6-114">Specifies the control protocol used in establishing a serial port communication for a <xref:System.IO.Ports.SerialPort> object.</span></span>|
|<xref:System.IO.Ports.Parity>|<span data-ttu-id="3ada6-115">Określa bit parzystości dla <xref:System.IO.Ports.SerialPort> obiektu.</span><span class="sxs-lookup"><span data-stu-id="3ada6-115">Specifies the parity bit for a <xref:System.IO.Ports.SerialPort> object.</span></span>|
|<xref:System.IO.Ports.SerialData>|<span data-ttu-id="3ada6-116">Określa typ znaku, który został odebrany przez port szeregowy <xref:System.IO.Ports.SerialPort> obiektu.</span><span class="sxs-lookup"><span data-stu-id="3ada6-116">Specifies the type of character that was received on the serial port of the <xref:System.IO.Ports.SerialPort> object.</span></span>|
|<xref:System.IO.Ports.SerialError>|<span data-ttu-id="3ada6-117">Określa błędy występujące w <xref:System.IO.Ports.SerialPort> obiekcie</span><span class="sxs-lookup"><span data-stu-id="3ada6-117">Specifies errors that occur on the <xref:System.IO.Ports.SerialPort> object</span></span>|
|<xref:System.IO.Ports.SerialPinChange>|<span data-ttu-id="3ada6-118">Określa typ zmiany, która wystąpiła w <xref:System.IO.Ports.SerialPort> obiekcie.</span><span class="sxs-lookup"><span data-stu-id="3ada6-118">Specifies the type of change that occurred on the <xref:System.IO.Ports.SerialPort> object.</span></span>|
|<xref:System.IO.Ports.StopBits>|<span data-ttu-id="3ada6-119">Określa liczbę bitów stopu używanych w <xref:System.IO.Ports.SerialPort> obiekcie.</span><span class="sxs-lookup"><span data-stu-id="3ada6-119">Specifies the number of stop bits used on the <xref:System.IO.Ports.SerialPort> object.</span></span>|

## <a name="see-also"></a><span data-ttu-id="3ada6-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3ada6-120">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- [<span data-ttu-id="3ada6-121">Uzyskiwanie dostępu do portów komputera</span><span class="sxs-lookup"><span data-stu-id="3ada6-121">Accessing the Computer's Ports</span></span>](accessing-the-computer-s-ports.md)
