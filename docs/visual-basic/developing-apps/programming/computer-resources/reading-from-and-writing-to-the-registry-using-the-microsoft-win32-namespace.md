---
title: Odczytywanie z oraz zapisywanie do rejestru za pomocą przestrzeni nazw Microsoft.Win32
ms.date: 07/20/2015
helpviewer_keywords:
- registry [Visual Basic]
ms.assetid: 4a0dcce0-c27b-4199-baa8-ee4528da6a56
ms.openlocfilehash: 841344186b8e56717b81e90397aabc608bdc6dab
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345498"
---
# <a name="reading-from-and-writing-to-the-registry-using-the-microsoftwin32-namespace-visual-basic"></a><span data-ttu-id="ef1c8-102">Odczytywanie z oraz zapisywanie do rejestru za pomocą przestrzeni nazw Microsoft.Win32 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ef1c8-102">Reading from and Writing to the Registry Using the Microsoft.Win32 Namespace (Visual Basic)</span></span>

<span data-ttu-id="ef1c8-103">Although `My.Computer.Registry` should cover your basic needs when programming against the registry, you can also use the <xref:Microsoft.Win32.Registry> and <xref:Microsoft.Win32.RegistryKey> classes in the <xref:Microsoft.Win32> namespace of the .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ef1c8-103">Although `My.Computer.Registry` should cover your basic needs when programming against the registry, you can also use the <xref:Microsoft.Win32.Registry> and <xref:Microsoft.Win32.RegistryKey> classes in the <xref:Microsoft.Win32> namespace of the .NET Framework.</span></span>  
  
## <a name="keys-in-the-registry-class"></a><span data-ttu-id="ef1c8-104">Keys in the Registry Class</span><span class="sxs-lookup"><span data-stu-id="ef1c8-104">Keys in the Registry Class</span></span>  

 <span data-ttu-id="ef1c8-105">The <xref:Microsoft.Win32.Registry> class supplies the base registry keys that can be used to access subkeys and their values.</span><span class="sxs-lookup"><span data-stu-id="ef1c8-105">The <xref:Microsoft.Win32.Registry> class supplies the base registry keys that can be used to access subkeys and their values.</span></span> <span data-ttu-id="ef1c8-106">The base keys themselves are read-only.</span><span class="sxs-lookup"><span data-stu-id="ef1c8-106">The base keys themselves are read-only.</span></span> <span data-ttu-id="ef1c8-107">The following table lists and describes the seven keys exposed by the <xref:Microsoft.Win32.Registry> class.</span><span class="sxs-lookup"><span data-stu-id="ef1c8-107">The following table lists and describes the seven keys exposed by the <xref:Microsoft.Win32.Registry> class.</span></span>  
  
|<span data-ttu-id="ef1c8-108">**Key**</span><span class="sxs-lookup"><span data-stu-id="ef1c8-108">**Key**</span></span>|<span data-ttu-id="ef1c8-109">**Opis**</span><span class="sxs-lookup"><span data-stu-id="ef1c8-109">**Description**</span></span>|  
|-------------|---------------------|  
|<xref:Microsoft.Win32.Registry.ClassesRoot>|<span data-ttu-id="ef1c8-110">Defines the types of documents and the properties associated with those types.</span><span class="sxs-lookup"><span data-stu-id="ef1c8-110">Defines the types of documents and the properties associated with those types.</span></span>|  
|<xref:Microsoft.Win32.Registry.CurrentConfig>|<span data-ttu-id="ef1c8-111">Contains hardware configuration information that is not user-specific.</span><span class="sxs-lookup"><span data-stu-id="ef1c8-111">Contains hardware configuration information that is not user-specific.</span></span>|  
|<xref:Microsoft.Win32.Registry.CurrentUser>|<span data-ttu-id="ef1c8-112">Contains information about the current user preferences, such as environmental variables.</span><span class="sxs-lookup"><span data-stu-id="ef1c8-112">Contains information about the current user preferences, such as environmental variables.</span></span>|  
|<xref:Microsoft.Win32.Registry.DynData>|<span data-ttu-id="ef1c8-113">Contains dynamic registry data, such as that used by Virtual Device Drivers.</span><span class="sxs-lookup"><span data-stu-id="ef1c8-113">Contains dynamic registry data, such as that used by Virtual Device Drivers.</span></span>|  
|<xref:Microsoft.Win32.Registry.LocalMachine>|<span data-ttu-id="ef1c8-114">Contains five subkeys (Hardware, SAM, Security, Software, and System) that hold the configuration data for the local computer.</span><span class="sxs-lookup"><span data-stu-id="ef1c8-114">Contains five subkeys (Hardware, SAM, Security, Software, and System) that hold the configuration data for the local computer.</span></span>|  
|<xref:Microsoft.Win32.Registry.PerformanceData>|<span data-ttu-id="ef1c8-115">Contains performance information for software components.</span><span class="sxs-lookup"><span data-stu-id="ef1c8-115">Contains performance information for software components.</span></span>|  
|<xref:Microsoft.Win32.Registry.Users>|<span data-ttu-id="ef1c8-116">Contains information about the default user preferences.</span><span class="sxs-lookup"><span data-stu-id="ef1c8-116">Contains information about the default user preferences.</span></span>|  
  
> [!IMPORTANT]
> <span data-ttu-id="ef1c8-117">It is more secure to write data to the current user (<xref:Microsoft.Win32.Registry.CurrentUser>) than to the local computer (<xref:Microsoft.Win32.Registry.LocalMachine>).</span><span class="sxs-lookup"><span data-stu-id="ef1c8-117">It is more secure to write data to the current user (<xref:Microsoft.Win32.Registry.CurrentUser>) than to the local computer (<xref:Microsoft.Win32.Registry.LocalMachine>).</span></span> <span data-ttu-id="ef1c8-118">A condition that's typically referred to as "squatting" occurs when the key you are creating was previously created by another, possibly malicious, process.</span><span class="sxs-lookup"><span data-stu-id="ef1c8-118">A condition that's typically referred to as "squatting" occurs when the key you are creating was previously created by another, possibly malicious, process.</span></span> <span data-ttu-id="ef1c8-119">To prevent this from occurring, use a method, such as <xref:Microsoft.Win32.RegistryKey.GetValue%2A>, that returns `Nothing` if the key does not already exist.</span><span class="sxs-lookup"><span data-stu-id="ef1c8-119">To prevent this from occurring, use a method, such as <xref:Microsoft.Win32.RegistryKey.GetValue%2A>, that returns `Nothing` if the key does not already exist.</span></span>  
  
## <a name="reading-a-value-from-the-registry"></a><span data-ttu-id="ef1c8-120">Reading a Value from the Registry</span><span class="sxs-lookup"><span data-stu-id="ef1c8-120">Reading a Value from the Registry</span></span>  

 <span data-ttu-id="ef1c8-121">The following code shows how to read a string from HKEY_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="ef1c8-121">The following code shows how to read a string from HKEY_CURRENT_USER.</span></span>  
  
 [!code-vb[VbResourceTasks#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#20)]  
  
 <span data-ttu-id="ef1c8-122">The following code reads, increments, and then writes a string to HKEY_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="ef1c8-122">The following code reads, increments, and then writes a string to HKEY_CURRENT_USER.</span></span>  
  
 [!code-vb[VbResourceTasks#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="ef1c8-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ef1c8-123">See also</span></span>

- <xref:System.SystemException>
- <xref:System.ApplicationException>
- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- [<span data-ttu-id="ef1c8-124">Try...Catch...Finally, instrukcja</span><span class="sxs-lookup"><span data-stu-id="ef1c8-124">Try...Catch...Finally Statement</span></span>](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="ef1c8-125">Odczytywanie z rejestru i zapisywanie w nim</span><span class="sxs-lookup"><span data-stu-id="ef1c8-125">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
- [<span data-ttu-id="ef1c8-126">Bezpieczeństwo i rejestr</span><span class="sxs-lookup"><span data-stu-id="ef1c8-126">Security and the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)
