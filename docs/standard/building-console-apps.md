---
title: Projektowanie aplikacji konsoli w programie .NET Framework
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .NET Framework, building console applications
- application development [.NET Framework], console
- console applications
ms.assetid: c21fb997-9f0e-40a5-8741-f73bba376bd8
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 8bcfa7d8a55cd2754965430db7ea6d2351892658
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="building-console-applications-in-the-net-framework"></a><span data-ttu-id="b6e28-102">Projektowanie aplikacji konsoli w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b6e28-102">Building Console Applications in the .NET Framework</span></span>
<span data-ttu-id="b6e28-103">Aplikacje w programie .NET Framework mogą używać <xref:System.Console?displayProperty=nameWithType> klasy odczytywanie znaków z i zapisywanie znaków do konsoli.</span><span class="sxs-lookup"><span data-stu-id="b6e28-103">Applications in the .NET Framework can use the <xref:System.Console?displayProperty=nameWithType> class to read characters from and write characters to the console.</span></span> <span data-ttu-id="b6e28-104">Dane z konsoli są odczytywane z Standardowy strumień wejściowy, dane w konsoli są zapisywane do standardowego strumienia wyjściowego, a dane błąd w konsoli są zapisywane do strumienia wyjściowego błąd standardowy.</span><span class="sxs-lookup"><span data-stu-id="b6e28-104">Data from the console is read from the standard input stream, data to the console is written to the standard output stream, and error data to the console is written to the standard error output stream.</span></span> <span data-ttu-id="b6e28-105">Tych strumieni są automatycznie kojarzone z konsoli po uruchomieniu aplikacji i są widoczne jako <xref:System.Console.In%2A>, <xref:System.Console.Out%2A>, i <xref:System.Console.Error%2A> właściwości, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="b6e28-105">These streams are automatically associated with the console when the application starts and are presented as the <xref:System.Console.In%2A>, <xref:System.Console.Out%2A>, and <xref:System.Console.Error%2A> properties, respectively.</span></span>  
  
 <span data-ttu-id="b6e28-106">Wartość <xref:System.Console.In%2A?displayProperty=nameWithType> właściwość jest <xref:System.IO.TextReader?displayProperty=nameWithType> obiektu, natomiast wartości <xref:System.Console.Out%2A?displayProperty=nameWithType> i <xref:System.Console.Error%2A?displayProperty=nameWithType> właściwości są <xref:System.IO.TextWriter?displayProperty=nameWithType> obiektów.</span><span class="sxs-lookup"><span data-stu-id="b6e28-106">The value of the <xref:System.Console.In%2A?displayProperty=nameWithType> property is a <xref:System.IO.TextReader?displayProperty=nameWithType> object, whereas the values of the <xref:System.Console.Out%2A?displayProperty=nameWithType> and <xref:System.Console.Error%2A?displayProperty=nameWithType> properties are <xref:System.IO.TextWriter?displayProperty=nameWithType> objects.</span></span> <span data-ttu-id="b6e28-107">Te właściwości można skojarzyć z strumieni, które nie reprezentują konsoli, umożliwiając punktu strumienia do innej lokalizacji dla danych wejściowych lub wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="b6e28-107">You can associate these properties with streams that do not represent the console, making it possible for you to point the stream to a different location for input or output.</span></span> <span data-ttu-id="b6e28-108">Na przykład przekierować dane wyjściowe do pliku przez ustawienie <xref:System.Console.Out%2A?displayProperty=nameWithType> właściwości <xref:System.IO.StreamWriter?displayProperty=nameWithType>, który hermetyzuje <xref:System.IO.FileStream?displayProperty=nameWithType> za pomocą klasy <xref:System.Console.SetOut%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="b6e28-108">For example, you can redirect the output to a file by setting the <xref:System.Console.Out%2A?displayProperty=nameWithType> property to a <xref:System.IO.StreamWriter?displayProperty=nameWithType>, which encapsulates a <xref:System.IO.FileStream?displayProperty=nameWithType> by means of the <xref:System.Console.SetOut%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="b6e28-109"><xref:System.Console.In%2A?displayProperty=nameWithType> i <xref:System.Console.Out%2A?displayProperty=nameWithType> właściwości nie muszą odwoływać się do tego samego strumienia.</span><span class="sxs-lookup"><span data-stu-id="b6e28-109">The <xref:System.Console.In%2A?displayProperty=nameWithType> and <xref:System.Console.Out%2A?displayProperty=nameWithType> properties do not need to refer to the same stream.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b6e28-110">Aby uzyskać więcej informacji dotyczących tworzenia aplikacji konsoli, w tym przykłady w języku C#, Visual Basic i C++, zobacz dokumentację <xref:System.Console> klasy.</span><span class="sxs-lookup"><span data-stu-id="b6e28-110">For more information about building console applications, including examples in C#, Visual Basic, and C++, see the documentation for the <xref:System.Console> class.</span></span>  
  
 <span data-ttu-id="b6e28-111">Jeśli konsola nie istnieje, tak jak aplikacji systemu Windows, dane wyjściowe zapisywane do standardowego strumienia wyjściowego nie będą widoczne, ponieważ nie mogła zapisać informacji do konsoli.</span><span class="sxs-lookup"><span data-stu-id="b6e28-111">If the console does not exist, as in a Windows-based application, output written to the standard output stream will not be visible, because there is no console to write the information to.</span></span> <span data-ttu-id="b6e28-112">Zapisywanie informacji o niedostępny konsoli nie powoduje wygenerowany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="b6e28-112">Writing information to an inaccessible console does not cause an exception to be raised.</span></span>  
  
 <span data-ttu-id="b6e28-113">Aby włączyć konsoli do odczytywania i zapisywania w aplikacji systemu Windows, który został utworzony przy użyciu programu Visual Studio, otwórz projekt **właściwości** okno dialogowe, kliknij przycisk **aplikacji** a następnie ustaw **typu aplikacji** do **aplikacji konsoli**.</span><span class="sxs-lookup"><span data-stu-id="b6e28-113">Alternately, to enable the console for reading and writing within a Windows-based application that is developed using Visual Studio, open the project's **Properties** dialog box, click the **Application** tab, and set the **Application type** to **Console Application**.</span></span>  
  
 <span data-ttu-id="b6e28-114">Aplikacje konsoli nie mają przekazywanie komunikatów, który uruchamia się domyślnie.</span><span class="sxs-lookup"><span data-stu-id="b6e28-114">Console applications lack a message pump that starts by default.</span></span> <span data-ttu-id="b6e28-115">W związku z tym wywołania konsoli Microsoft Win32 czasomierze może zakończyć się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="b6e28-115">Therefore, console calls to Microsoft Win32 timers might fail.</span></span>  
  
 <span data-ttu-id="b6e28-116">**System.Console** klasa zawiera metody, które mogą odczytywać znaki lub całe wiersze z konsoli.</span><span class="sxs-lookup"><span data-stu-id="b6e28-116">The **System.Console** class has methods that can read individual characters or entire lines from the console.</span></span> <span data-ttu-id="b6e28-117">Inne metody Konwertowanie ciągów danych i format, a następnie wpisz ciągi sformatowane do konsoli.</span><span class="sxs-lookup"><span data-stu-id="b6e28-117">Other methods convert data and format strings, and then write the formatted strings to the console.</span></span> <span data-ttu-id="b6e28-118">Aby uzyskać więcej informacji na ciągach formatowania, zobacz [typy formatowania](../../docs/standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="b6e28-118">For more information on formatting strings, see [Formatting Types](../../docs/standard/base-types/formatting-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6e28-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b6e28-119">See Also</span></span>  
 <xref:System.Console?displayProperty=nameWithType>  
 [<span data-ttu-id="b6e28-120">Formatowanie typów</span><span class="sxs-lookup"><span data-stu-id="b6e28-120">Formatting Types</span></span>](../../docs/standard/base-types/formatting-types.md)
