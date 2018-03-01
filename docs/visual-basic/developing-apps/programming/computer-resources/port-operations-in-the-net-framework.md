---
title: "Operacje związane z portem w oprogramowaniu .NET Framework przeprowadzane za pomocą Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- ports, Visual Basic
ms.assetid: 1eba223b-7bd3-401a-b097-982bce96df1b
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 77b8a464f2f64f701a5b99690756c0f22a410064
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="port-operations-in-the-net-framework-with-visual-basic"></a><span data-ttu-id="56494-102">Operacje związane z portem w oprogramowaniu .NET Framework przeprowadzane za pomocą Visual Basic</span><span class="sxs-lookup"><span data-stu-id="56494-102">Port Operations in the .NET Framework with Visual Basic</span></span>
<span data-ttu-id="56494-103">Są dostępne porty szeregowe komputera za pośrednictwem [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] klas w <xref:System.IO.Ports?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="56494-103">You can access your computer's serial ports through the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] classes in the <xref:System.IO.Ports?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="56494-104">Najważniejsze klasy <xref:System.IO.Ports.SerialPort>, dostarcza strukturę dla synchroniczne i sterowane zdarzeniami we/wy, dostępu do numeru pin i podział stanów i dostęp do właściwości szeregowego sterownika.</span><span class="sxs-lookup"><span data-stu-id="56494-104">The most important class, <xref:System.IO.Ports.SerialPort>, provides a framework for synchronous and event-driven I/O, access to pin and break states, and access to serial driver properties.</span></span> <span data-ttu-id="56494-105">Może być ujęte w <xref:System.IO.Stream> obiektu dostępny za pośrednictwem <xref:System.IO.Ports.SerialPort.BaseStream> właściwości.</span><span class="sxs-lookup"><span data-stu-id="56494-105">It can be wrapped in a <xref:System.IO.Stream> object, accessible through the <xref:System.IO.Ports.SerialPort.BaseStream> property.</span></span> <span data-ttu-id="56494-106">Zawijanie <xref:System.IO.Ports.SerialPort> w <xref:System.IO.Stream> obiekt umożliwia portu szeregowego były dostępne dla klasy, które używają strumieni.</span><span class="sxs-lookup"><span data-stu-id="56494-106">Wrapping <xref:System.IO.Ports.SerialPort> in a <xref:System.IO.Stream> object allows the serial port to be accessed by classes that use streams.</span></span> <span data-ttu-id="56494-107">Ta przestrzeń nazw obejmuje wyliczenia, które ułatwiają kontrolę nad porty szeregowe.</span><span class="sxs-lookup"><span data-stu-id="56494-107">The namespace includes enumerations that simplify the control of serial ports.</span></span>  
  
 <span data-ttu-id="56494-108">Najprostszym sposobem tworzenia <xref:System.IO.Ports.SerialPort> obiekt jest za pośrednictwem <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="56494-108">The simplest way to create a <xref:System.IO.Ports.SerialPort> object is through the <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A> method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="56494-109">Nie można użyć [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] klasy bezpośredni dostęp do innych portów, takich jak porty równoległe, portów USB i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="56494-109">You cannot use [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] classes to directly access other types of ports, such as parallel ports, USB ports, and so on.</span></span>  
  
## <a name="enumerations"></a><span data-ttu-id="56494-110">Wyliczenia</span><span class="sxs-lookup"><span data-stu-id="56494-110">Enumerations</span></span>  
 <span data-ttu-id="56494-111">W tej tabeli wymieniono i opisano główny wyliczenia, używane do uzyskiwania dostępu do portu szeregowego:</span><span class="sxs-lookup"><span data-stu-id="56494-111">This table lists and describes the main enumerations used for accessing a serial port:</span></span>  
  
|<span data-ttu-id="56494-112">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="56494-112">Enumeration</span></span>|<span data-ttu-id="56494-113">Opis</span><span class="sxs-lookup"><span data-stu-id="56494-113">Description</span></span>|  
|---|---|   
|<xref:System.IO.Ports.Handshake>|<span data-ttu-id="56494-114">Określa używany podczas ustanawiania komunikacji portu szeregowego, dla protokołu sterowania <xref:System.IO.Ports.SerialPort> obiektu.</span><span class="sxs-lookup"><span data-stu-id="56494-114">Specifies the control protocol used in establishing a serial port communication for a <xref:System.IO.Ports.SerialPort> object.</span></span>|  
|<xref:System.IO.Ports.Parity>|<span data-ttu-id="56494-115">Określa bit parzystości dla <xref:System.IO.Ports.SerialPort> obiektu.</span><span class="sxs-lookup"><span data-stu-id="56494-115">Specifies the parity bit for a <xref:System.IO.Ports.SerialPort> object.</span></span>|  
|<xref:System.IO.Ports.SerialData>|<span data-ttu-id="56494-116">Określa typ znak, który został odebrany w portu szeregowego <xref:System.IO.Ports.SerialPort> obiektu.</span><span class="sxs-lookup"><span data-stu-id="56494-116">Specifies the type of character that was received on the serial port of the <xref:System.IO.Ports.SerialPort> object.</span></span>|  
|<xref:System.IO.Ports.SerialError>|<span data-ttu-id="56494-117">Określa błędów występujących na <xref:System.IO.Ports.SerialPort> obiektu</span><span class="sxs-lookup"><span data-stu-id="56494-117">Specifies errors that occur on the <xref:System.IO.Ports.SerialPort> object</span></span>|  
|<xref:System.IO.Ports.SerialPinChange>|<span data-ttu-id="56494-118">Określa typ zmiany, który wystąpił na <xref:System.IO.Ports.SerialPort> obiektu.</span><span class="sxs-lookup"><span data-stu-id="56494-118">Specifies the type of change that occurred on the <xref:System.IO.Ports.SerialPort> object.</span></span>|  
|<xref:System.IO.Ports.StopBits>|<span data-ttu-id="56494-119">Określa liczbę bitów stopu używane na <xref:System.IO.Ports.SerialPort> obiektu.</span><span class="sxs-lookup"><span data-stu-id="56494-119">Specifies the number of stop bits used on the <xref:System.IO.Ports.SerialPort> object.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="56494-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="56494-120">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Devices.Ports>  
 [<span data-ttu-id="56494-121">Uzyskiwanie dostępu do portów komputera</span><span class="sxs-lookup"><span data-stu-id="56494-121">Accessing the Computer's Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-computer-s-ports.md)
