---
title: Odczytywanie z rejestru i zapisywanie w nim
ms.date: 07/20/2015
helpviewer_keywords:
- My.Computer.Registry object, tasks
- registry [Visual Basic], writing to
- registry [Visual Basic], reading
ms.assetid: a13da106-185b-41d7-b23c-416da65e21e4
ms.openlocfilehash: 89db9ef9db4235c069d6239d32e4f8679fbabf0b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74349762"
---
# <a name="reading-from-and-writing-to-the-registry-visual-basic"></a><span data-ttu-id="15d3b-102">Odczytywanie z oraz zapisywanie do rejestru (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="15d3b-102">Reading from and Writing to the Registry (Visual Basic)</span></span>

<span data-ttu-id="15d3b-103">W tym temacie opisano tematy dotyczące zadań i pojęć, które są skojarzone z rejestrem.</span><span class="sxs-lookup"><span data-stu-id="15d3b-103">This topic describes task and conceptual topics that are associated with the registry.</span></span>  
  
 <span data-ttu-id="15d3b-104">Podczas programowania w Visual Basic można wybrać dostęp do rejestru za pomocą funkcji udostępnianych przez Visual Basic lub klasy rejestru .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="15d3b-104">When programming in Visual Basic, you can choose to access the registry by means of either the functions provided by Visual Basic or the registry classes of the .NET Framework.</span></span> <span data-ttu-id="15d3b-105">Rejestr zawiera informacje z systemu operacyjnego oraz informacje z aplikacji hostowanych na komputerze.</span><span class="sxs-lookup"><span data-stu-id="15d3b-105">The registry hosts information from the operating system as well as information from applications hosted on the machine.</span></span> <span data-ttu-id="15d3b-106">Praca z rejestrem może naruszyć bezpieczeństwo przez umożliwienie nieodpowiedniego dostępu do zasobów systemowych lub chronionych informacji.</span><span class="sxs-lookup"><span data-stu-id="15d3b-106">Working with the registry may compromise security by allowing inappropriate access to system resources or protected information.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="15d3b-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="15d3b-107">In This Section</span></span>  

 [<span data-ttu-id="15d3b-108">Instrukcje: tworzenie klucza rejestru i określanie jego wartości</span><span class="sxs-lookup"><span data-stu-id="15d3b-108">How to: Create a Registry Key and Set Its Value</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-create-a-registry-key-and-set-its-value.md)  
 <span data-ttu-id="15d3b-109">Opisuje sposób użycia metod `CreateSubKey` i `SetValue` `My.Computer.Registry` obiektu do utworzenia klucza rejestru i ustawienia jego wartości.</span><span class="sxs-lookup"><span data-stu-id="15d3b-109">Describes how to use the `CreateSubKey` and `SetValue` methods of the `My.Computer.Registry` object to create a registry key and set its value.</span></span>  
  
 [<span data-ttu-id="15d3b-110">Instrukcje: odczytywanie wartości z klucza rejestru</span><span class="sxs-lookup"><span data-stu-id="15d3b-110">How to: Read a Value from a Registry Key</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-read-a-value-from-a-registry-key.md)  
 <span data-ttu-id="15d3b-111">Opisuje sposób użycia `GetValue` metody `My.Computer.Registry` obiektu do odczytania wartości z klucza rejestru.</span><span class="sxs-lookup"><span data-stu-id="15d3b-111">Describes how to use the `GetValue` method of the `My.Computer.Registry` object to read a value from a registry key.</span></span>  
  
 [<span data-ttu-id="15d3b-112">Instrukcje: usuwanie klucza rejestru</span><span class="sxs-lookup"><span data-stu-id="15d3b-112">How to: Delete a Registry Key</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-delete-a-registry-key.md)  
 <span data-ttu-id="15d3b-113">Opisuje sposób użycia `DeleteSubKey` metody `My.Computer.Registry.CurrentUser` właściwości w celu usunięcia klucza rejestru.</span><span class="sxs-lookup"><span data-stu-id="15d3b-113">Describes how to use the `DeleteSubKey` method of the `My.Computer.Registry.CurrentUser` property to delete a registry key.</span></span>  
  
 [<span data-ttu-id="15d3b-114">Odczytywanie z rejestru i zapisywanie w nim za pomocą przestrzeni nazw Microsoft.Win32</span><span class="sxs-lookup"><span data-stu-id="15d3b-114">Reading from and Writing to the Registry Using the Microsoft.Win32 Namespace</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry-using-the-microsoft-win32-namespace.md)  
 <span data-ttu-id="15d3b-115">Opisuje sposób używania klas `Registry` i `RegistryKey` .NET Framework, aby uzyskać dostęp do rejestru.</span><span class="sxs-lookup"><span data-stu-id="15d3b-115">Describes how to use the `Registry` and `RegistryKey` classes of the .NET Framework to access the registry.</span></span>  
  
 [<span data-ttu-id="15d3b-116">Bezpieczeństwo i rejestr</span><span class="sxs-lookup"><span data-stu-id="15d3b-116">Security and the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)  
 <span data-ttu-id="15d3b-117">Omawia problemy z zabezpieczeniami związane z rejestrem.</span><span class="sxs-lookup"><span data-stu-id="15d3b-117">Discusses security issues involving the registry.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="15d3b-118">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="15d3b-118">Related Sections</span></span>  

 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>  
 <span data-ttu-id="15d3b-119">Wyświetla listę i objaśnia elementy członkowskie `My.Computer.Registry` obiektu.</span><span class="sxs-lookup"><span data-stu-id="15d3b-119">Lists and explains members of the `My.Computer.Registry` object.</span></span>  
  
 <xref:Microsoft.Win32.Registry>  
 <span data-ttu-id="15d3b-120">Przedstawia przegląd `Registry` klasy wraz z łączami do poszczególnych kluczy i członków.</span><span class="sxs-lookup"><span data-stu-id="15d3b-120">Presents an overview of the `Registry` class, along with links to individual keys and members.</span></span>
