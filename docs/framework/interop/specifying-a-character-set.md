---
title: "Określanie zestawu znaków"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- platform invoke, attribute fields
- attribute fields in platform invoke, CharSet
- CharSet field
ms.assetid: a8347eb1-295f-46b9-8a78-63331f9ecc50
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3e97c640472156c1a47ad125bffeaf39b8eb0762
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="specifying-a-character-set"></a><span data-ttu-id="abdc6-102">Określanie zestawu znaków</span><span class="sxs-lookup"><span data-stu-id="abdc6-102">Specifying a Character Set</span></span>
<span data-ttu-id="abdc6-103"><xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> Pola określa ciąg organizowanie i określa, jak wywołanie nazwy funkcji znalezione w bibliotece DLL platformy.</span><span class="sxs-lookup"><span data-stu-id="abdc6-103">The <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field controls string marshaling and determines how platform invoke finds function names in a DLL.</span></span> <span data-ttu-id="abdc6-104">W tym temacie opisano zarówno zachowania.</span><span class="sxs-lookup"><span data-stu-id="abdc6-104">This topic describes both behaviors.</span></span>  
  
 <span data-ttu-id="abdc6-105">Niektóre funkcje interfejsu API wyeksportować dwie wersje funkcji, które przyjmują argumenty typu string: wąskie (ANSI) i sieci (Unicode).</span><span class="sxs-lookup"><span data-stu-id="abdc6-105">Some APIs export two versions of functions that take string arguments: narrow (ANSI) and wide (Unicode).</span></span> <span data-ttu-id="abdc6-106">Interfejs API Win32, na przykład obejmuje następujące nazwy punktu wejścia dla **MessageBox** funkcji:</span><span class="sxs-lookup"><span data-stu-id="abdc6-106">The Win32 API, for instance, includes the following entry-point names for the **MessageBox** function:</span></span>  
  
-   <span data-ttu-id="abdc6-107">**MessageBoxA**</span><span class="sxs-lookup"><span data-stu-id="abdc6-107">**MessageBoxA**</span></span>  
  
     <span data-ttu-id="abdc6-108">Udostępnia 1-bajtowych wartości znakowych formatowania ANSI, rozróżnianych na podstawie "A" dodanym na końcu nazwy punktu wejścia.</span><span class="sxs-lookup"><span data-stu-id="abdc6-108">Provides 1-byte character ANSI formatting, distinguished by an "A" appended to the entry-point name.</span></span> <span data-ttu-id="abdc6-109">Wywołuje się **MessageBoxA** zawsze sformatować kierowanie ciągów ANSI, jak często na platformach Windows 95 i Windows 98.</span><span class="sxs-lookup"><span data-stu-id="abdc6-109">Calls to **MessageBoxA** always marshal strings in ANSI format, as is common on Windows 95 and Windows 98 platforms.</span></span>  
  
-   <span data-ttu-id="abdc6-110">**MessageBoxW**</span><span class="sxs-lookup"><span data-stu-id="abdc6-110">**MessageBoxW**</span></span>  
  
     <span data-ttu-id="abdc6-111">Udostępnia 2-bajtowych wartości znakowych Unicode formatowania, rozróżnianych na podstawie "W" dodanym na końcu nazwy punktu wejścia.</span><span class="sxs-lookup"><span data-stu-id="abdc6-111">Provides 2-byte character Unicode formatting, distinguished by a "W" appended to the entry-point name.</span></span> <span data-ttu-id="abdc6-112">Wywołuje się **MessageBoxW** zawsze kierować ciągi w formacie Unicode, jak często na platformach Windows NT, Windows 2000 i Windows XP.</span><span class="sxs-lookup"><span data-stu-id="abdc6-112">Calls to **MessageBoxW** always marshal strings in Unicode format, as is common on Windows NT, Windows 2000, and Windows XP platforms.</span></span>  
  
## <a name="string-marshaling-and-name-matching"></a><span data-ttu-id="abdc6-113">Organizowanie ciągów i dopasowywanie nazw</span><span class="sxs-lookup"><span data-stu-id="abdc6-113">String Marshaling and Name Matching</span></span>  
 <span data-ttu-id="abdc6-114">**CharSet** pole przyjmuje następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="abdc6-114">The **CharSet** field accepts the following values:</span></span>  
  
 <span data-ttu-id="abdc6-115">**CharSet.Ansi** (wartość domyślna)</span><span class="sxs-lookup"><span data-stu-id="abdc6-115">**CharSet.Ansi** (default value)</span></span>  
  
-   <span data-ttu-id="abdc6-116">Ciąg organizowanie</span><span class="sxs-lookup"><span data-stu-id="abdc6-116">String marshaling</span></span>  
  
     <span data-ttu-id="abdc6-117">Wywołanie platformy ciągów marshals z ich format zarządzanych (Unicode) do formatu ANSI.</span><span class="sxs-lookup"><span data-stu-id="abdc6-117">Platform invoke marshals strings from their managed format (Unicode) to ANSI format.</span></span>  
  
-   <span data-ttu-id="abdc6-118">Dopasowywanie nazw</span><span class="sxs-lookup"><span data-stu-id="abdc6-118">Name matching</span></span>  
  
     <span data-ttu-id="abdc6-119">Gdy <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType> pole jest **true**, ponieważ jest domyślnie w [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], wyszukuje tylko nazwa nadana wywołanie platformy.</span><span class="sxs-lookup"><span data-stu-id="abdc6-119">When the <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType> field is **true**, as it is by default in [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], platform invoke searches only for the name you specify.</span></span> <span data-ttu-id="abdc6-120">Na przykład jeśli określisz **MessageBox**, wywołanie platformy wyszukuje **MessageBox** i kończy się niepowodzeniem, gdy nie można odnaleźć dokładnej pisowni.</span><span class="sxs-lookup"><span data-stu-id="abdc6-120">For example, if you specify **MessageBox**, platform invoke searches for **MessageBox** and fails when it cannot locate the exact spelling.</span></span>  
  
     <span data-ttu-id="abdc6-121">Gdy **opcję ExactSpelling** pole jest **false**, ponieważ jest domyślnie w C++ i C#, wywołanie platformy wyszukuje unmangled alias najpierw (**MessageBox**), następnie (nazwa zniekształcona **MessageBoxA**) Jeśli nie zostanie znaleziony unmangled alias.</span><span class="sxs-lookup"><span data-stu-id="abdc6-121">When the **ExactSpelling** field is **false**, as it is by default in C++ and C#, platform invoke searches for the unmangled alias first (**MessageBox**), then the mangled name (**MessageBoxA**) if the unmangled alias is not found.</span></span> <span data-ttu-id="abdc6-122">Zwróć uwagę, że zachowanie Dopasowywanie nazw ANSI różni się od zachowania Dopasowywanie nazw Unicode.</span><span class="sxs-lookup"><span data-stu-id="abdc6-122">Notice that ANSI name-matching behavior differs from Unicode name-matching behavior.</span></span>  
  
 <span data-ttu-id="abdc6-123">**Wartość CharSet.Unicode**</span><span class="sxs-lookup"><span data-stu-id="abdc6-123">**CharSet.Unicode**</span></span>  
  
-   <span data-ttu-id="abdc6-124">Ciąg organizowanie</span><span class="sxs-lookup"><span data-stu-id="abdc6-124">String marshaling</span></span>  
  
     <span data-ttu-id="abdc6-125">Wywołanie platformy ciągów kopie z ich format zarządzanych (Unicode) na Unicode format.</span><span class="sxs-lookup"><span data-stu-id="abdc6-125">Platform invoke copies strings from their managed format (Unicode) to Unicode format.</span></span>  
  
-   <span data-ttu-id="abdc6-126">Dopasowywanie nazw</span><span class="sxs-lookup"><span data-stu-id="abdc6-126">Name matching</span></span>  
  
     <span data-ttu-id="abdc6-127">Gdy **opcję ExactSpelling** pole jest **true**, ponieważ jest domyślnie w [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], wyszukuje tylko nazwa nadana wywołanie platformy.</span><span class="sxs-lookup"><span data-stu-id="abdc6-127">When the **ExactSpelling** field is **true**, as it is by default in [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], platform invoke searches only for the name you specify.</span></span> <span data-ttu-id="abdc6-128">Na przykład jeśli określisz **MessageBox**, wywołanie platformy wyszukuje **MessageBox** i kończy się niepowodzeniem, jeśli nie można zlokalizować dokładnej pisowni.</span><span class="sxs-lookup"><span data-stu-id="abdc6-128">For example, if you specify **MessageBox**, platform invoke searches for **MessageBox** and fails if it cannot locate the exact spelling.</span></span>  
  
     <span data-ttu-id="abdc6-129">Gdy **opcję ExactSpelling** pole jest **false**, ponieważ jest domyślnie w C++ i C#, wywołanie platformy wyszukuje nazwa zniekształcona najpierw (**MessageBoxW**), następnie unmangled aliasu (**MessageBox**) Jeśli nie zostanie znaleziona taka nazwa zniekształcona.</span><span class="sxs-lookup"><span data-stu-id="abdc6-129">When the **ExactSpelling** field is **false**, as it is by default in C++ and C#, platform invoke searches for the mangled name first (**MessageBoxW**), then the unmangled alias (**MessageBox**) if the mangled name is not found.</span></span> <span data-ttu-id="abdc6-130">Zwróć uwagę, że zachowanie Dopasowywanie nazw Unicode różni się od zachowania Dopasowywanie nazw ANSI.</span><span class="sxs-lookup"><span data-stu-id="abdc6-130">Notice that Unicode name-matching behavior differs from ANSI name-matching behavior.</span></span>  
  
 <span data-ttu-id="abdc6-131">**CharSet.Auto**</span><span class="sxs-lookup"><span data-stu-id="abdc6-131">**CharSet.Auto**</span></span>  
  
-   <span data-ttu-id="abdc6-132">Wywołanie platformy wybierze między ANSI i Unicode formaty w czasie wykonywania, oparte na platformie docelowej.</span><span class="sxs-lookup"><span data-stu-id="abdc6-132">Platform invoke chooses between ANSI and Unicode formats at run time, based on the target platform.</span></span>  
  
## <a name="specifying-a-character-set-in-visual-basic"></a><span data-ttu-id="abdc6-133">Określanie zestawu znaków w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="abdc6-133">Specifying a Character Set in Visual Basic</span></span>  
 <span data-ttu-id="abdc6-134">Poniższy przykład deklaruje **MessageBox** funkcja trzy razy, zawsze z inaczej zestawu znaków.</span><span class="sxs-lookup"><span data-stu-id="abdc6-134">The following example declares the **MessageBox** function three times, each time with different character-set behavior.</span></span> <span data-ttu-id="abdc6-135">Można określić zachowanie zestawu znaków w języku Visual Basic, dodając **Ansi**, **Unicode**, lub **automatycznie** — słowo kluczowe do instrukcji deklaracji.</span><span class="sxs-lookup"><span data-stu-id="abdc6-135">You can specify character-set behavior in Visual Basic by adding the **Ansi**, **Unicode**, or **Auto** keyword to the declaration statement.</span></span>  
  
 <span data-ttu-id="abdc6-136">W przypadku pominięcia kluczowego zestawu znaków, co jest wykonywane w pierwszej instrukcji deklaracji <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> pola wartość domyślna to zestaw znaków ANSI.</span><span class="sxs-lookup"><span data-stu-id="abdc6-136">If you omit the character-set keyword, as is done in the first declaration statement, the <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field defaults to the ANSI character set.</span></span> <span data-ttu-id="abdc6-137">Drugi i trzeci instrukcje w tym przykładzie jawnie określić zestaw ze słowem kluczowym znaków.</span><span class="sxs-lookup"><span data-stu-id="abdc6-137">The second and third statements in the example explicitly specify a character set with a keyword.</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
  
Public Class Win32  
   Declare Function MessageBoxA Lib "user32.dll"(ByVal hWnd As Integer, _  
       ByVal txt As String, ByVal caption As String, _  
       ByVal Typ As Integer) As Integer  
  
   Declare Unicode Function MessageBoxW Lib "user32.dll" _  
       (ByVal hWnd As Integer, ByVal txt As String, _  
        ByVal caption As String, ByVal Typ As Integer) As Integer  
  
   Declare Auto Function MessageBox Lib "user32.dll" _  
       (ByVal hWnd As Integer, ByVal txt As String, _  
        ByVal caption As String, ByVal Typ As Integer) As Integer  
End Class  
```  
  
## <a name="specifying-a-character-set-in-c-and-c"></a><span data-ttu-id="abdc6-138">Określanie zestawu znaków w języku C# i C++</span><span class="sxs-lookup"><span data-stu-id="abdc6-138">Specifying a Character Set in C# and C++</span></span>  
 <span data-ttu-id="abdc6-139"><xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> Pole określa podstawowy zestaw znaków jako ANSI lub Unicode.</span><span class="sxs-lookup"><span data-stu-id="abdc6-139">The <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field identifies the underlying character set as ANSI or Unicode.</span></span> <span data-ttu-id="abdc6-140">Formanty, jak można zorganizować argumenty typu string do metody zestawu znaków.</span><span class="sxs-lookup"><span data-stu-id="abdc6-140">The character set controls how string arguments to a method should be marshaled.</span></span> <span data-ttu-id="abdc6-141">Do wskazania zestawu znaków, należy użyć jednej z następujących formatów:</span><span class="sxs-lookup"><span data-stu-id="abdc6-141">Use one of the following forms to indicate the character set:</span></span>  
  
```csharp  
[DllImport("dllname", CharSet=CharSet.Ansi)]  
[DllImport("dllname", CharSet=CharSet.Unicode)]  
[DllImport("dllname", CharSet=CharSet.Auto)]  
```  
  
```cpp  
[DllImport("dllname", CharSet=CharSet::Ansi)]  
[DllImport("dllname", CharSet=CharSet::Unicode)]  
[DllImport("dllname", CharSet=CharSet::Auto)]  
```  
  
 <span data-ttu-id="abdc6-142">W poniższym przykładzie przedstawiono trzy zarządzanych definicje **MessageBox** funkcji przypisanych do określenia zestawu znaków.</span><span class="sxs-lookup"><span data-stu-id="abdc6-142">The following example shows three managed definitions of the **MessageBox** function attributed to specify a character set.</span></span> <span data-ttu-id="abdc6-143">W pierwszym definicji, przez jej pominięcia **CharSet** pola wartość domyślna to zestaw znaków ANSI.</span><span class="sxs-lookup"><span data-stu-id="abdc6-143">In the first definition, by its omission, the **CharSet** field defaults to the ANSI character set.</span></span>  
  
```csharp  
[DllImport("user32.dll")]  
    public static extern int MessageBoxA(int hWnd, String text,   
        String caption, uint type);  
[DllImport("user32.dll", CharSet=CharSet.Unicode)]  
    public static extern int MessageBoxW(int hWnd, String text,   
        String caption, uint type);  
[DllImport("user32.dll", CharSet=CharSet.Auto)]  
    public static extern int MessageBox(int hWnd, String text,   
        String caption, uint type);  
```  
  
```cpp  
typedef void* HWND;  
  
//Can use MessageBox or MessageBoxA.  
[DllImport("user32")]  
extern "C" int MessageBox(HWND hWnd,  
                          String* pText,  
                          String* pCaption,  
                          unsigned int uType);  
  
//Can use MessageBox or MessageBoxW.  
[DllImport("user32", CharSet=CharSet::Unicode)]  
extern "C" int MessageBoxW(HWND hWnd,  
                          String* pText,  
                          String* pCaption,  
                          unsigned int uType);  
  
//Must use MessageBox.  
[DllImport("user32", CharSet=CharSet::Auto)]  
extern "C" int MessageBox(HWND hWnd,  
                          String* pText,  
                          String* pCaption,  
                          unsigned int uType);  
```  
  
## <a name="see-also"></a><span data-ttu-id="abdc6-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="abdc6-144">See Also</span></span>  
 <xref:System.Runtime.InteropServices.DllImportAttribute>  
 [<span data-ttu-id="abdc6-145">Tworzenie prototypów w kodzie zarządzanym</span><span class="sxs-lookup"><span data-stu-id="abdc6-145">Creating Prototypes in Managed Code</span></span>](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)  
 [<span data-ttu-id="abdc6-146">Przykłady wywołań platformy</span><span class="sxs-lookup"><span data-stu-id="abdc6-146">Platform Invoke Examples</span></span>](../../../docs/framework/interop/platform-invoke-examples.md)  
 [<span data-ttu-id="abdc6-147">Marshaling danych w wywołaniu platformy</span><span class="sxs-lookup"><span data-stu-id="abdc6-147">Marshaling Data with Platform Invoke</span></span>](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)
