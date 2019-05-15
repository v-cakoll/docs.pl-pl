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
# <a name="port-operations-in-the-net-framework-with-visual-basic"></a><span data-ttu-id="9e212-102">Operacje związane z portem w oprogramowaniu .NET Framework przeprowadzane za pomocą Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9e212-102">Port Operations in the .NET Framework with Visual Basic</span></span>
<span data-ttu-id="9e212-103">Dostęp do portów szeregowych na komputerze przy użyciu klas .NET Framework w <xref:System.IO.Ports?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="9e212-103">You can access your computer's serial ports through the .NET Framework classes in the <xref:System.IO.Ports?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="9e212-104">Najważniejsze klasy <xref:System.IO.Ports.SerialPort>, zapewnia ramy pozwalające synchroniczne i oparte na zdarzeniach operacji We/Wy, dostępu stanom pin i podziału i dostęp do właściwości sterownika szeregowe.</span><span class="sxs-lookup"><span data-stu-id="9e212-104">The most important class, <xref:System.IO.Ports.SerialPort>, provides a framework for synchronous and event-driven I/O, access to pin and break states, and access to serial driver properties.</span></span> <span data-ttu-id="9e212-105">Mogą być ujęte w <xref:System.IO.Stream> obiekt, za pośrednictwem <xref:System.IO.Ports.SerialPort.BaseStream> właściwości.</span><span class="sxs-lookup"><span data-stu-id="9e212-105">It can be wrapped in a <xref:System.IO.Stream> object, accessible through the <xref:System.IO.Ports.SerialPort.BaseStream> property.</span></span> <span data-ttu-id="9e212-106">Zawijanie <xref:System.IO.Ports.SerialPort> w <xref:System.IO.Stream> obiekt umożliwia portu szeregowego dostępu do klasy, które używają strumieni.</span><span class="sxs-lookup"><span data-stu-id="9e212-106">Wrapping <xref:System.IO.Ports.SerialPort> in a <xref:System.IO.Stream> object allows the serial port to be accessed by classes that use streams.</span></span> <span data-ttu-id="9e212-107">Przestrzeń nazw zawiera wyliczenia, które ułatwiają kontrolę nad portów szeregowych.</span><span class="sxs-lookup"><span data-stu-id="9e212-107">The namespace includes enumerations that simplify the control of serial ports.</span></span>  
  
 <span data-ttu-id="9e212-108">Najprostszym sposobem utworzenia <xref:System.IO.Ports.SerialPort> obiekt jest za pośrednictwem <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="9e212-108">The simplest way to create a <xref:System.IO.Ports.SerialPort> object is through the <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A> method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9e212-109">Nie można użyć klas .NET Framework w celu uzyskania bezpośredniego dostępu do innych typów porty, na przykład portów równoległych, portów USB i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="9e212-109">You cannot use .NET Framework classes to directly access other types of ports, such as parallel ports, USB ports, and so on.</span></span>  
  
## <a name="enumerations"></a><span data-ttu-id="9e212-110">Wyliczenia</span><span class="sxs-lookup"><span data-stu-id="9e212-110">Enumerations</span></span>  
 <span data-ttu-id="9e212-111">W tej tabeli wymieniono i opisano główne wyliczenia używane do uzyskiwania dostępu do portu szeregowego:</span><span class="sxs-lookup"><span data-stu-id="9e212-111">This table lists and describes the main enumerations used for accessing a serial port:</span></span>  
  
|<span data-ttu-id="9e212-112">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="9e212-112">Enumeration</span></span>|<span data-ttu-id="9e212-113">Opis</span><span class="sxs-lookup"><span data-stu-id="9e212-113">Description</span></span>|  
|---|---|   
|<xref:System.IO.Ports.Handshake>|<span data-ttu-id="9e212-114">Określa protokół kontroli używany podczas ustanawiania port szeregowy komunikacji dla <xref:System.IO.Ports.SerialPort> obiektu.</span><span class="sxs-lookup"><span data-stu-id="9e212-114">Specifies the control protocol used in establishing a serial port communication for a <xref:System.IO.Ports.SerialPort> object.</span></span>|  
|<xref:System.IO.Ports.Parity>|<span data-ttu-id="9e212-115">Określa bitu parzystości do <xref:System.IO.Ports.SerialPort> obiektu.</span><span class="sxs-lookup"><span data-stu-id="9e212-115">Specifies the parity bit for a <xref:System.IO.Ports.SerialPort> object.</span></span>|  
|<xref:System.IO.Ports.SerialData>|<span data-ttu-id="9e212-116">Określa typ znaku, który został odebrany przez port szeregowy z <xref:System.IO.Ports.SerialPort> obiektu.</span><span class="sxs-lookup"><span data-stu-id="9e212-116">Specifies the type of character that was received on the serial port of the <xref:System.IO.Ports.SerialPort> object.</span></span>|  
|<xref:System.IO.Ports.SerialError>|<span data-ttu-id="9e212-117">Określa błędów występujących na <xref:System.IO.Ports.SerialPort> obiektu</span><span class="sxs-lookup"><span data-stu-id="9e212-117">Specifies errors that occur on the <xref:System.IO.Ports.SerialPort> object</span></span>|  
|<xref:System.IO.Ports.SerialPinChange>|<span data-ttu-id="9e212-118">Określa typ zmiany, która wystąpiła w <xref:System.IO.Ports.SerialPort> obiektu.</span><span class="sxs-lookup"><span data-stu-id="9e212-118">Specifies the type of change that occurred on the <xref:System.IO.Ports.SerialPort> object.</span></span>|  
|<xref:System.IO.Ports.StopBits>|<span data-ttu-id="9e212-119">Określa liczbę bitów stop na <xref:System.IO.Ports.SerialPort> obiektu.</span><span class="sxs-lookup"><span data-stu-id="9e212-119">Specifies the number of stop bits used on the <xref:System.IO.Ports.SerialPort> object.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9e212-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9e212-120">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- [<span data-ttu-id="9e212-121">Uzyskiwanie dostępu do portów komputera</span><span class="sxs-lookup"><span data-stu-id="9e212-121">Accessing the Computer's Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-computer-s-ports.md)
