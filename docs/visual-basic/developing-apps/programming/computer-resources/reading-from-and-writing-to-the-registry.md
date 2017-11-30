---
title: Odczytywanie z oraz zapisywanie do rejestru (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- My.Computer.Registry object, tasks
- registry [Visual Basic], writing to
- registry [Visual Basic], reading
ms.assetid: a13da106-185b-41d7-b23c-416da65e21e4
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: db564b428d585829b220674271f4636bfcc68562
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="reading-from-and-writing-to-the-registry-visual-basic"></a><span data-ttu-id="dd1de-102">Odczytywanie z oraz zapisywanie do rejestru (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dd1de-102">Reading from and Writing to the Registry (Visual Basic)</span></span>
<span data-ttu-id="dd1de-103">W tym temacie opisano zadania i tematy dotyczące pojęć, które są skojarzone z rejestru.</span><span class="sxs-lookup"><span data-stu-id="dd1de-103">This topic describes task and conceptual topics that are associated with the registry.</span></span>  
  
 <span data-ttu-id="dd1de-104">Programowania w [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], użytkownik może uzyskać dostępu do rejestru za pomocą funkcje udostępniane przez [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] lub klasy rejestru programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="dd1de-104">When programming in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], you can choose to access the registry by means of either the functions provided by [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] or the registry classes of the .NET Framework.</span></span> <span data-ttu-id="dd1de-105">Informacje rejestru hostów z systemu operacyjnego, a także informacji z aplikacji uruchamianych na komputerze.</span><span class="sxs-lookup"><span data-stu-id="dd1de-105">The registry hosts information from the operating system as well as information from applications hosted on the machine.</span></span> <span data-ttu-id="dd1de-106">Praca z rejestru może naruszyć bezpieczeństwo, zezwalając nieodpowiednie dostęp do zasobów systemowych lub chronionych informacji.</span><span class="sxs-lookup"><span data-stu-id="dd1de-106">Working with the registry may compromise security by allowing inappropriate access to system resources or protected information.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dd1de-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="dd1de-107">In This Section</span></span>  
 [<span data-ttu-id="dd1de-108">Porady: Tworzenie klucza rejestru i ustaw jej wartość</span><span class="sxs-lookup"><span data-stu-id="dd1de-108">How to: Create a Registry Key and Set Its Value</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-create-a-registry-key-and-set-its-value.md)  
 <span data-ttu-id="dd1de-109">Informacje dotyczące używania `CreateSubKey` i `SetValue` metody `My.Computer.Registry` obiekt do tworzenia klucza rejestru i ustaw jej wartość.</span><span class="sxs-lookup"><span data-stu-id="dd1de-109">Describes how to use the `CreateSubKey` and `SetValue` methods of the `My.Computer.Registry` object to create a registry key and set its value.</span></span>  
  
 [<span data-ttu-id="dd1de-110">Porady: odczytywanie wartości z klucza rejestru</span><span class="sxs-lookup"><span data-stu-id="dd1de-110">How to: Read a Value from a Registry Key</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-read-a-value-from-a-registry-key.md)  
 <span data-ttu-id="dd1de-111">Informacje dotyczące używania `GetValue` metody `My.Computer.Registry` obiektu odczytać wartości z klucza rejestru.</span><span class="sxs-lookup"><span data-stu-id="dd1de-111">Describes how to use the `GetValue` method of the `My.Computer.Registry` object to read a value from a registry key.</span></span>  
  
 [<span data-ttu-id="dd1de-112">Porady: usuwanie klucza rejestru</span><span class="sxs-lookup"><span data-stu-id="dd1de-112">How to: Delete a Registry Key</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-delete-a-registry-key.md)  
 <span data-ttu-id="dd1de-113">Informacje dotyczące używania `DeleteSubKey` metody `My.Computer.Registry.CurrentUser` właściwości można usunąć klucza rejestru.</span><span class="sxs-lookup"><span data-stu-id="dd1de-113">Describes how to use the `DeleteSubKey` method of the `My.Computer.Registry.CurrentUser` property to delete a registry key.</span></span>  
  
 [<span data-ttu-id="dd1de-114">Odczytywanie z oraz zapisywanie do rejestru za pomocą Namespace Microsoft.Win32</span><span class="sxs-lookup"><span data-stu-id="dd1de-114">Reading from and Writing to the Registry Using the Microsoft.Win32 Namespace</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry-using-the-microsoft-win32-namespace.md)  
 <span data-ttu-id="dd1de-115">Informacje dotyczące używania `Registry` i `RegistryKey` klasy [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] dostępu do rejestru.</span><span class="sxs-lookup"><span data-stu-id="dd1de-115">Describes how to use the `Registry` and `RegistryKey` classes of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] to access the registry.</span></span>  
  
 [<span data-ttu-id="dd1de-116">Bezpieczeństwo i rejestr</span><span class="sxs-lookup"><span data-stu-id="dd1de-116">Security and the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)  
 <span data-ttu-id="dd1de-117">W tym artykule omówiono problemy z zabezpieczeniami dotyczące rejestru.</span><span class="sxs-lookup"><span data-stu-id="dd1de-117">Discusses security issues involving the registry.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="dd1de-118">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="dd1de-118">Related Sections</span></span>  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>  
 <span data-ttu-id="dd1de-119">Wymieniono i opisano elementy członkowskie `My.Computer.Registry` obiektu.</span><span class="sxs-lookup"><span data-stu-id="dd1de-119">Lists and explains members of the `My.Computer.Registry` object.</span></span>  
  
 <xref:Microsoft.Win32.Registry>  
 <span data-ttu-id="dd1de-120">Zawiera omówienie programu `Registry` klasy oraz łącza do poszczególnych kluczy i elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="dd1de-120">Presents an overview of the `Registry` class, along with links to individual keys and members.</span></span>
