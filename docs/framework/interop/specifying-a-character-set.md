---
title: Określanie zestawu znaków
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- platform invoke, attribute fields
- attribute fields in platform invoke, CharSet
- CharSet field
ms.assetid: a8347eb1-295f-46b9-8a78-63331f9ecc50
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 798fcacab5bd74dbd6569a68a3b598c0bb63a0a7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61872641"
---
# <a name="specifying-a-character-set"></a><span data-ttu-id="86283-102">Określanie zestawu znaków</span><span class="sxs-lookup"><span data-stu-id="86283-102">Specifying a Character Set</span></span>
<span data-ttu-id="86283-103"><xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> Pole kontroluje kierowanie ciągu i określa, jak wywołanie platformy znajduje nazwy funkcji w bibliotece DLL.</span><span class="sxs-lookup"><span data-stu-id="86283-103">The <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field controls string marshaling and determines how platform invoke finds function names in a DLL.</span></span> <span data-ttu-id="86283-104">W tym temacie opisano obie zachowania.</span><span class="sxs-lookup"><span data-stu-id="86283-104">This topic describes both behaviors.</span></span>  
  
 <span data-ttu-id="86283-105">Niektóre interfejsy API wyeksportować dwie wersje funkcji, które przyjmują argumenty typu string: wąskiego (ANSI) i dwubajtowych (Unicode).</span><span class="sxs-lookup"><span data-stu-id="86283-105">Some APIs export two versions of functions that take string arguments: narrow (ANSI) and wide (Unicode).</span></span> <span data-ttu-id="86283-106">Interfejs API Windows, na przykład zawiera następujące nazwy punktu wejścia dla **MessageBox** funkcji:</span><span class="sxs-lookup"><span data-stu-id="86283-106">The Windows API, for instance, includes the following entry-point names for the **MessageBox** function:</span></span>  
  
- <span data-ttu-id="86283-107">**MessageBoxA**</span><span class="sxs-lookup"><span data-stu-id="86283-107">**MessageBoxA**</span></span>  
  
     <span data-ttu-id="86283-108">Zawiera formatowanie ANSI 1-bajtowych wartości znakowych rozróżnianych na podstawie "A", po której dołączany do wybranej nazwy punktu wejścia.</span><span class="sxs-lookup"><span data-stu-id="86283-108">Provides 1-byte character ANSI formatting, distinguished by an "A" appended to the entry-point name.</span></span> <span data-ttu-id="86283-109">Wywołania **MessageBoxA** zawsze przeprowadzanie marshalingu ciągów w formacie ANSI.</span><span class="sxs-lookup"><span data-stu-id="86283-109">Calls to **MessageBoxA** always marshal strings in ANSI format.</span></span>  
  
- <span data-ttu-id="86283-110">**MessageBoxW**</span><span class="sxs-lookup"><span data-stu-id="86283-110">**MessageBoxW**</span></span>  
  
     <span data-ttu-id="86283-111">Zawiera formatowanie 2-bajtowych wartości znakowych Unicode, rozróżnianych na podstawie "W" dołączany do wybranej nazwy punktu wejścia.</span><span class="sxs-lookup"><span data-stu-id="86283-111">Provides 2-byte character Unicode formatting, distinguished by a "W" appended to the entry-point name.</span></span> <span data-ttu-id="86283-112">Wywołania **MessageBoxW** zawsze przeprowadzanie marshalingu ciągów w formacie Unicode.</span><span class="sxs-lookup"><span data-stu-id="86283-112">Calls to **MessageBoxW** always marshal strings in Unicode format.</span></span>  
  
## <a name="string-marshaling-and-name-matching"></a><span data-ttu-id="86283-113">Marshaling ciągów i dopasowywanie nazw</span><span class="sxs-lookup"><span data-stu-id="86283-113">String Marshaling and Name Matching</span></span>  
 <span data-ttu-id="86283-114">`CharSet` Pole akceptuje następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="86283-114">The `CharSet` field accepts the following values:</span></span>  
  
 <span data-ttu-id="86283-115"><xref:System.Runtime.InteropServices.CharSet.Ansi> (wartość domyślna)</span><span class="sxs-lookup"><span data-stu-id="86283-115"><xref:System.Runtime.InteropServices.CharSet.Ansi> (default value)</span></span>  
  
- <span data-ttu-id="86283-116">Ciąg marshalingu</span><span class="sxs-lookup"><span data-stu-id="86283-116">String marshaling</span></span>  
  
     <span data-ttu-id="86283-117">Wywołanie platformy marshals ciągi z ich formatu zarządzanych (Unicode) na ANSI format.</span><span class="sxs-lookup"><span data-stu-id="86283-117">Platform invoke marshals strings from their managed format (Unicode) to ANSI format.</span></span>  
  
- <span data-ttu-id="86283-118">Dopasowywanie nazw</span><span class="sxs-lookup"><span data-stu-id="86283-118">Name matching</span></span>  
  
     <span data-ttu-id="86283-119">Gdy <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType> pole jest `true`, ponieważ jest on domyślnie [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], wyszukuje tylko należy określić nazwę wywołania platformy.</span><span class="sxs-lookup"><span data-stu-id="86283-119">When the <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType> field is `true`, as it is by default in [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], platform invoke searches only for the name you specify.</span></span> <span data-ttu-id="86283-120">Na przykład, jeśli określisz **MessageBox**, wyszukuje wywołania platformy **MessageBox** i kończy się niepowodzeniem, gdy nie można odnaleźć dokładnej pisowni.</span><span class="sxs-lookup"><span data-stu-id="86283-120">For example, if you specify **MessageBox**, platform invoke searches for **MessageBox** and fails when it cannot locate the exact spelling.</span></span>  
  
     <span data-ttu-id="86283-121">Gdy `ExactSpelling` pole jest `false`, ponieważ jest ona domyślnie w języku C++ i C#, pierwsze wywołanie platformy wyszukuje unmangled aliasu (**MessageBox**), następnie zniekształcone nazwy (**MessageBoxA**) Jeśli nie zostanie znaleziony unmangled aliasu.</span><span class="sxs-lookup"><span data-stu-id="86283-121">When the `ExactSpelling` field is `false`, as it is by default in C++ and C#, platform invoke searches for the unmangled alias first (**MessageBox**), then the mangled name (**MessageBoxA**) if the unmangled alias is not found.</span></span> <span data-ttu-id="86283-122">Należy zauważyć, że zachowanie Dopasowywanie nazw ANSI różni się od zachowania Dopasowywanie nazw Unicode.</span><span class="sxs-lookup"><span data-stu-id="86283-122">Notice that ANSI name-matching behavior differs from Unicode name-matching behavior.</span></span>  
  
 <xref:System.Runtime.InteropServices.CharSet.Unicode>  
  
- <span data-ttu-id="86283-123">Ciąg marshalingu</span><span class="sxs-lookup"><span data-stu-id="86283-123">String marshaling</span></span>  
  
     <span data-ttu-id="86283-124">Wywołanie platformy ciągi kopie z ich formatu zarządzanych (Unicode) do formatu Unicode.</span><span class="sxs-lookup"><span data-stu-id="86283-124">Platform invoke copies strings from their managed format (Unicode) to Unicode format.</span></span>  
  
- <span data-ttu-id="86283-125">Dopasowywanie nazw</span><span class="sxs-lookup"><span data-stu-id="86283-125">Name matching</span></span>  
  
     <span data-ttu-id="86283-126">Gdy `ExactSpelling` pole jest `true`, ponieważ jest on domyślnie [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], wyszukuje tylko należy określić nazwę wywołania platformy.</span><span class="sxs-lookup"><span data-stu-id="86283-126">When the `ExactSpelling` field is `true`, as it is by default in [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], platform invoke searches only for the name you specify.</span></span> <span data-ttu-id="86283-127">Na przykład, jeśli określisz **MessageBox**, wyszukuje wywołania platformy **MessageBox** i kończy się niepowodzeniem, jeśli nie może zlokalizować dokładnej pisowni.</span><span class="sxs-lookup"><span data-stu-id="86283-127">For example, if you specify **MessageBox**, platform invoke searches for **MessageBox** and fails if it cannot locate the exact spelling.</span></span>  
  
     <span data-ttu-id="86283-128">Gdy `ExactSpelling` pole jest `false`, ponieważ jest ona domyślnie w języku C++ i C#, pierwsze wywołanie platformy wyszukuje zniekształcone nazwy (**MessageBoxW**), następnie unmangled aliasu (**MessageBox**) Jeśli nie znaleziono zniekształcone nazwy.</span><span class="sxs-lookup"><span data-stu-id="86283-128">When the `ExactSpelling` field is `false`, as it is by default in C++ and C#, platform invoke searches for the mangled name first (**MessageBoxW**), then the unmangled alias (**MessageBox**) if the mangled name is not found.</span></span> <span data-ttu-id="86283-129">Należy zauważyć, że zachowanie Dopasowywanie nazw Unicode różni się od zachowania Dopasowywanie nazw ANSI.</span><span class="sxs-lookup"><span data-stu-id="86283-129">Notice that Unicode name-matching behavior differs from ANSI name-matching behavior.</span></span>  
  
 <xref:System.Runtime.InteropServices.CharSet.Auto>  
  
- <span data-ttu-id="86283-130">Wywołanie platformy wybiera między ANSI i Unicode formaty w czasie wykonywania, oparte na platformie docelowej.</span><span class="sxs-lookup"><span data-stu-id="86283-130">Platform invoke chooses between ANSI and Unicode formats at run time, based on the target platform.</span></span>  
  
## <a name="specifying-a-character-set-in-visual-basic"></a><span data-ttu-id="86283-131">Określanie zestawu znaków w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="86283-131">Specifying a Character Set in Visual Basic</span></span>  
 <span data-ttu-id="86283-132">Poniższy przykład deklaruje **MessageBox** funkcja trzy razy, każdorazowo przy użyciu różnych zachowanie zestawu znaków.</span><span class="sxs-lookup"><span data-stu-id="86283-132">The following example declares the **MessageBox** function three times, each time with different character-set behavior.</span></span> <span data-ttu-id="86283-133">Można określić zachowanie zestawu znaków w języku Visual Basic, dodając **Ansi**, **Unicode**, lub **automatycznie** — słowo kluczowe do instrukcji deklaracji.</span><span class="sxs-lookup"><span data-stu-id="86283-133">You can specify character-set behavior in Visual Basic by adding the **Ansi**, **Unicode**, or **Auto** keyword to the declaration statement.</span></span>  
  
 <span data-ttu-id="86283-134">Jeżeli pominięto słowa kluczowego zestaw znaków, jak odbywa się w pierwszej instrukcji deklaracji <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> pola wartość domyślna to zestawu znaków ANSI.</span><span class="sxs-lookup"><span data-stu-id="86283-134">If you omit the character-set keyword, as is done in the first declaration statement, the <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field defaults to the ANSI character set.</span></span> <span data-ttu-id="86283-135">Drugi i trzeci instrukcji w przykładzie jawnie określić znak, który został ustawiony za pomocą słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="86283-135">The second and third statements in the example explicitly specify a character set with a keyword.</span></span>  
  
```vb
Imports System

Friend Class WindowsAPI
    Friend Shared Declare Function MessageBoxA Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer

    Friend Shared Declare Unicode Function MessageBoxW Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer

    Friend Shared Declare Auto Function MessageBox Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
End Class
```
  
## <a name="specifying-a-character-set-in-c-and-c"></a><span data-ttu-id="86283-136">Określanie zestawu znaków w C# i C++</span><span class="sxs-lookup"><span data-stu-id="86283-136">Specifying a Character Set in C# and C++</span></span>  
 <span data-ttu-id="86283-137"><xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> Pole identyfikuje podstawowy zestaw znaków jako ANSI lub Unicode.</span><span class="sxs-lookup"><span data-stu-id="86283-137">The <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field identifies the underlying character set as ANSI or Unicode.</span></span> <span data-ttu-id="86283-138">Formanty, jak powinny być wprowadzane argumenty typu string do metody zestawu znaków.</span><span class="sxs-lookup"><span data-stu-id="86283-138">The character set controls how string arguments to a method should be marshaled.</span></span> <span data-ttu-id="86283-139">Aby wskazać zestaw znaków, użyj jednej z następujących form:</span><span class="sxs-lookup"><span data-stu-id="86283-139">Use one of the following forms to indicate the character set:</span></span>  
  
```csharp
[DllImport("DllName", CharSet = CharSet.Ansi)]
[DllImport("DllName", CharSet = CharSet.Unicode)]
[DllImport("DllName", CharSet = CharSet.Auto)]
```
  
```cpp
[DllImport("DllName", CharSet = CharSet::Ansi)]
[DllImport("DllName", CharSet = CharSet::Unicode)]
[DllImport("DllName", CharSet = CharSet::Auto)]
```
  
 <span data-ttu-id="86283-140">W poniższym przykładzie przedstawiono trzy definicje zarządzanych **MessageBox** opartego na atrybutach funkcji do określenia zestawu znaków.</span><span class="sxs-lookup"><span data-stu-id="86283-140">The following example shows three managed definitions of the **MessageBox** function attributed to specify a character set.</span></span> <span data-ttu-id="86283-141">W pierwszym definicji przez jej pominięcia `CharSet` pola wartość domyślna to zestawu znaków ANSI.</span><span class="sxs-lookup"><span data-stu-id="86283-141">In the first definition, by its omission, the `CharSet` field defaults to the ANSI character set.</span></span>  
  
```csharp  
using System;
using System.Runtime.InteropServices;

internal static class WindowsAPI
{
    [DllImport("user32.dll")]
    internal static extern int MessageBoxA(
        IntPtr hWnd, string lpText, string lpCaption, uint uType);

    [DllImport("user32.dll", CharSet = CharSet.Unicode)]
    internal static extern int MessageBoxW(
        IntPtr hWnd, string lpText, string lpCaption, uint uType);

    [DllImport("user32.dll", CharSet = CharSet.Auto)]
    internal static extern int MessageBox(
        IntPtr hWnd, string lpText, string lpCaption, uint uType);
}
```  
  
```cpp
typedef void* HWND;

// Can use MessageBox or MessageBoxA.
[DllImport("user32")]
extern "C" int MessageBox(
    HWND hWnd, String* lpText, String* lpCaption, unsigned int uType);

// Can use MessageBox or MessageBoxW.
[DllImport("user32", CharSet = CharSet::Unicode)]
extern "C" int MessageBoxW(
    HWND hWnd, String* lpText, String* lpCaption, unsigned int uType);

// Must use MessageBox.
[DllImport("user32", CharSet = CharSet::Auto)]
extern "C" int MessageBox(
    HWND hWnd, String* lpText, String* lpCaption, unsigned int uType);
```
  
## <a name="see-also"></a><span data-ttu-id="86283-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="86283-142">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [<span data-ttu-id="86283-143">Tworzenie prototypów w kodzie zarządzanym</span><span class="sxs-lookup"><span data-stu-id="86283-143">Creating Prototypes in Managed Code</span></span>](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="86283-144">Przykłady wywołań platformy</span><span class="sxs-lookup"><span data-stu-id="86283-144">Platform Invoke Examples</span></span>](../../../docs/framework/interop/platform-invoke-examples.md)
- [<span data-ttu-id="86283-145">Marshaling danych w wywołaniu platformy</span><span class="sxs-lookup"><span data-stu-id="86283-145">Marshaling Data with Platform Invoke</span></span>](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)
