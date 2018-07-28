---
title: Odczytywanie z oraz zapisywanie do rejestru (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.Computer.Registry object, tasks
- registry [Visual Basic], writing to
- registry [Visual Basic], reading
ms.assetid: a13da106-185b-41d7-b23c-416da65e21e4
ms.openlocfilehash: 6ce05b956ebf9a544eb8c95165b0f709c694f334
ms.sourcegitcommit: 869b5832b667915ac4a5dd8c86b1109ed26b6c08
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/28/2018
ms.locfileid: "39332938"
---
# <a name="reading-from-and-writing-to-the-registry-visual-basic"></a><span data-ttu-id="50dd7-102">Odczytywanie z oraz zapisywanie do rejestru (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="50dd7-102">Reading from and Writing to the Registry (Visual Basic)</span></span>
<span data-ttu-id="50dd7-103">W tym temacie opisano zadania i pojęć, które są skojarzone z rejestru.</span><span class="sxs-lookup"><span data-stu-id="50dd7-103">This topic describes task and conceptual topics that are associated with the registry.</span></span>  
  
 <span data-ttu-id="50dd7-104">Podczas programowania w języku Visual Basic, można uzyskać dostępu do rejestru za pomocą funkcji Visual Basic lub klasy rejestru programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="50dd7-104">When programming in Visual Basic, you can choose to access the registry by means of either the functions provided by Visual Basic or the registry classes of the .NET Framework.</span></span> <span data-ttu-id="50dd7-105">Informacje o hostach rejestru z systemu operacyjnego, a także informacji z aplikacji znajdującej się na komputerze.</span><span class="sxs-lookup"><span data-stu-id="50dd7-105">The registry hosts information from the operating system as well as information from applications hosted on the machine.</span></span> <span data-ttu-id="50dd7-106">Praca z rejestru może naruszyć bezpieczeństwo, zezwalając na niewłaściwe dostęp do zasobów systemowych lub informacje chronione.</span><span class="sxs-lookup"><span data-stu-id="50dd7-106">Working with the registry may compromise security by allowing inappropriate access to system resources or protected information.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="50dd7-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="50dd7-107">In This Section</span></span>  
 [<span data-ttu-id="50dd7-108">Instrukcje: tworzenie klucza rejestru i określanie jego wartości</span><span class="sxs-lookup"><span data-stu-id="50dd7-108">How to: Create a Registry Key and Set Its Value</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-create-a-registry-key-and-set-its-value.md)  
 <span data-ttu-id="50dd7-109">Opisuje sposób używania `CreateSubKey` i `SetValue` metody `My.Computer.Registry` obiekt do tworzenia klucza rejestru i określanie jego wartości.</span><span class="sxs-lookup"><span data-stu-id="50dd7-109">Describes how to use the `CreateSubKey` and `SetValue` methods of the `My.Computer.Registry` object to create a registry key and set its value.</span></span>  
  
 [<span data-ttu-id="50dd7-110">Instrukcje: odczytywanie wartości z klucza rejestru</span><span class="sxs-lookup"><span data-stu-id="50dd7-110">How to: Read a Value from a Registry Key</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-read-a-value-from-a-registry-key.md)  
 <span data-ttu-id="50dd7-111">Opisuje sposób używania `GetValue` metody `My.Computer.Registry` obiektu można odczytać wartości z klucza rejestru.</span><span class="sxs-lookup"><span data-stu-id="50dd7-111">Describes how to use the `GetValue` method of the `My.Computer.Registry` object to read a value from a registry key.</span></span>  
  
 [<span data-ttu-id="50dd7-112">Instrukcje: usuwanie klucza rejestru</span><span class="sxs-lookup"><span data-stu-id="50dd7-112">How to: Delete a Registry Key</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-delete-a-registry-key.md)  
 <span data-ttu-id="50dd7-113">Opisuje sposób używania `DeleteSubKey` metody `My.Computer.Registry.CurrentUser` właściwości można usunąć klucza rejestru.</span><span class="sxs-lookup"><span data-stu-id="50dd7-113">Describes how to use the `DeleteSubKey` method of the `My.Computer.Registry.CurrentUser` property to delete a registry key.</span></span>  
  
 [<span data-ttu-id="50dd7-114">Odczytywanie z rejestru i zapisywanie w nim za pomocą przestrzeni nazw Microsoft.Win32</span><span class="sxs-lookup"><span data-stu-id="50dd7-114">Reading from and Writing to the Registry Using the Microsoft.Win32 Namespace</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry-using-the-microsoft-win32-namespace.md)  
 <span data-ttu-id="50dd7-115">Opisuje sposób używania `Registry` i `RegistryKey` klasy [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] dostępu do rejestru.</span><span class="sxs-lookup"><span data-stu-id="50dd7-115">Describes how to use the `Registry` and `RegistryKey` classes of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] to access the registry.</span></span>  
  
 [<span data-ttu-id="50dd7-116">Bezpieczeństwo i rejestr</span><span class="sxs-lookup"><span data-stu-id="50dd7-116">Security and the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)  
 <span data-ttu-id="50dd7-117">W tym artykule omówiono problemy dotyczące zabezpieczeń obejmujące rejestru.</span><span class="sxs-lookup"><span data-stu-id="50dd7-117">Discusses security issues involving the registry.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="50dd7-118">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="50dd7-118">Related Sections</span></span>  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>  
 <span data-ttu-id="50dd7-119">Przedstawiono oraz wyjaśniono członkowie `My.Computer.Registry` obiektu.</span><span class="sxs-lookup"><span data-stu-id="50dd7-119">Lists and explains members of the `My.Computer.Registry` object.</span></span>  
  
 <xref:Microsoft.Win32.Registry>  
 <span data-ttu-id="50dd7-120">Przedstawia omówienie `Registry` klasy, wraz z linkami do poszczególnych kluczy i elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="50dd7-120">Presents an overview of the `Registry` class, along with links to individual keys and members.</span></span>
