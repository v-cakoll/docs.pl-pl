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
ms.openlocfilehash: 45810390ced8584ea7b37908a9e4af8d3da73f34
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54549853"
---
# <a name="specifying-a-character-set"></a><span data-ttu-id="faf88-102">Określanie zestawu znaków</span><span class="sxs-lookup"><span data-stu-id="faf88-102">Specifying a Character Set</span></span>
<span data-ttu-id="faf88-103"><xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> Pole kontroluje kierowanie ciągu i określa, jak wywołanie platformy znajduje nazwy funkcji w bibliotece DLL.</span><span class="sxs-lookup"><span data-stu-id="faf88-103">The <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field controls string marshaling and determines how platform invoke finds function names in a DLL.</span></span> <span data-ttu-id="faf88-104">W tym temacie opisano obie zachowania.</span><span class="sxs-lookup"><span data-stu-id="faf88-104">This topic describes both behaviors.</span></span>  
  
 <span data-ttu-id="faf88-105">Niektóre interfejsy API wyeksportować dwie wersje funkcji, które przyjmują argumenty typu string: wąskiego (ANSI) i dwubajtowych (Unicode).</span><span class="sxs-lookup"><span data-stu-id="faf88-105">Some APIs export two versions of functions that take string arguments: narrow (ANSI) and wide (Unicode).</span></span> <span data-ttu-id="faf88-106">Win32 API zawiera na przykład następujące nazwy punktu wejścia dla **MessageBox** funkcji:</span><span class="sxs-lookup"><span data-stu-id="faf88-106">The Win32 API, for instance, includes the following entry-point names for the **MessageBox** function:</span></span>  
  
-   <span data-ttu-id="faf88-107">**MessageBoxA**</span><span class="sxs-lookup"><span data-stu-id="faf88-107">**MessageBoxA**</span></span>  
  
     <span data-ttu-id="faf88-108">Zawiera formatowanie ANSI 1-bajtowych wartości znakowych rozróżnianych na podstawie "A", po której dołączany do wybranej nazwy punktu wejścia.</span><span class="sxs-lookup"><span data-stu-id="faf88-108">Provides 1-byte character ANSI formatting, distinguished by an "A" appended to the entry-point name.</span></span> <span data-ttu-id="faf88-109">Wywołania **MessageBoxA** zawsze sformatować przeprowadzanie marshalingu ciągów ANSI, co jest często spotykane na platformach Windows 95 i Windows 98.</span><span class="sxs-lookup"><span data-stu-id="faf88-109">Calls to **MessageBoxA** always marshal strings in ANSI format, as is common on Windows 95 and Windows 98 platforms.</span></span>  
  
-   <span data-ttu-id="faf88-110">**MessageBoxW**</span><span class="sxs-lookup"><span data-stu-id="faf88-110">**MessageBoxW**</span></span>  
  
     <span data-ttu-id="faf88-111">Zawiera formatowanie 2-bajtowych wartości znakowych Unicode, rozróżnianych na podstawie "W" dołączany do wybranej nazwy punktu wejścia.</span><span class="sxs-lookup"><span data-stu-id="faf88-111">Provides 2-byte character Unicode formatting, distinguished by a "W" appended to the entry-point name.</span></span> <span data-ttu-id="faf88-112">Wywołania **MessageBoxW** zawsze przeprowadzanie marshalingu ciągów w formacie Unicode, co jest często spotykane na platformach Windows NT, Windows 2000 i Windows XP.</span><span class="sxs-lookup"><span data-stu-id="faf88-112">Calls to **MessageBoxW** always marshal strings in Unicode format, as is common on Windows NT, Windows 2000, and Windows XP platforms.</span></span>  
  
## <a name="string-marshaling-and-name-matching"></a><span data-ttu-id="faf88-113">Marshaling ciągów i dopasowywanie nazw</span><span class="sxs-lookup"><span data-stu-id="faf88-113">String Marshaling and Name Matching</span></span>  
 <span data-ttu-id="faf88-114">**CharSet** pole akceptuje następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="faf88-114">The **CharSet** field accepts the following values:</span></span>  
  
 <span data-ttu-id="faf88-115">**CharSet.Ansi** (wartość domyślna)</span><span class="sxs-lookup"><span data-stu-id="faf88-115">**CharSet.Ansi** (default value)</span></span>  
  
-   <span data-ttu-id="faf88-116">Ciąg marshalingu</span><span class="sxs-lookup"><span data-stu-id="faf88-116">String marshaling</span></span>  
  
     <span data-ttu-id="faf88-117">Wywołanie platformy marshals ciągi z ich formatu zarządzanych (Unicode) na ANSI format.</span><span class="sxs-lookup"><span data-stu-id="faf88-117">Platform invoke marshals strings from their managed format (Unicode) to ANSI format.</span></span>  
  
-   <span data-ttu-id="faf88-118">Dopasowywanie nazw</span><span class="sxs-lookup"><span data-stu-id="faf88-118">Name matching</span></span>  
  
     <span data-ttu-id="faf88-119">Gdy <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType> pole jest **true**, ponieważ jest ona domyślnie w [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], wyszukuje tylko należy określić nazwę wywołania platformy.</span><span class="sxs-lookup"><span data-stu-id="faf88-119">When the <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType> field is **true**, as it is by default in [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], platform invoke searches only for the name you specify.</span></span> <span data-ttu-id="faf88-120">Na przykład, jeśli określisz **MessageBox**, wyszukuje wywołania platformy **MessageBox** i kończy się niepowodzeniem, gdy nie można odnaleźć dokładnej pisowni.</span><span class="sxs-lookup"><span data-stu-id="faf88-120">For example, if you specify **MessageBox**, platform invoke searches for **MessageBox** and fails when it cannot locate the exact spelling.</span></span>  
  
     <span data-ttu-id="faf88-121">Gdy **ExactSpelling** pole jest **false**, ponieważ jest ona domyślnie w języku C++ i C#, pierwsze wywołanie platformy wyszukuje unmangled aliasu (**MessageBox**), a następnie zniekształcone nazwy (**MessageBoxA**) Jeśli nie zostanie znaleziony unmangled aliasu.</span><span class="sxs-lookup"><span data-stu-id="faf88-121">When the **ExactSpelling** field is **false**, as it is by default in C++ and C#, platform invoke searches for the unmangled alias first (**MessageBox**), then the mangled name (**MessageBoxA**) if the unmangled alias is not found.</span></span> <span data-ttu-id="faf88-122">Należy zauważyć, że zachowanie Dopasowywanie nazw ANSI różni się od zachowania Dopasowywanie nazw Unicode.</span><span class="sxs-lookup"><span data-stu-id="faf88-122">Notice that ANSI name-matching behavior differs from Unicode name-matching behavior.</span></span>  
  
 <span data-ttu-id="faf88-123">**CharSet.Unicode**</span><span class="sxs-lookup"><span data-stu-id="faf88-123">**CharSet.Unicode**</span></span>  
  
-   <span data-ttu-id="faf88-124">Ciąg marshalingu</span><span class="sxs-lookup"><span data-stu-id="faf88-124">String marshaling</span></span>  
  
     <span data-ttu-id="faf88-125">Wywołanie platformy ciągi kopie z ich formatu zarządzanych (Unicode) do formatu Unicode.</span><span class="sxs-lookup"><span data-stu-id="faf88-125">Platform invoke copies strings from their managed format (Unicode) to Unicode format.</span></span>  
  
-   <span data-ttu-id="faf88-126">Dopasowywanie nazw</span><span class="sxs-lookup"><span data-stu-id="faf88-126">Name matching</span></span>  
  
     <span data-ttu-id="faf88-127">Gdy **ExactSpelling** pole jest **true**, ponieważ jest ona domyślnie w [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], wyszukuje tylko należy określić nazwę wywołania platformy.</span><span class="sxs-lookup"><span data-stu-id="faf88-127">When the **ExactSpelling** field is **true**, as it is by default in [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], platform invoke searches only for the name you specify.</span></span> <span data-ttu-id="faf88-128">Na przykład, jeśli określisz **MessageBox**, wyszukuje wywołania platformy **MessageBox** i kończy się niepowodzeniem, jeśli nie może zlokalizować dokładnej pisowni.</span><span class="sxs-lookup"><span data-stu-id="faf88-128">For example, if you specify **MessageBox**, platform invoke searches for **MessageBox** and fails if it cannot locate the exact spelling.</span></span>  
  
     <span data-ttu-id="faf88-129">Gdy **ExactSpelling** pole jest **false**, ponieważ jest ona domyślnie w języku C++ i C#, pierwsze wywołanie platformy wyszukuje zniekształcone nazwy (**MessageBoxW**), a następnie unmangled alias (**MessageBox**) Jeśli nie znaleziono zniekształcone nazwy.</span><span class="sxs-lookup"><span data-stu-id="faf88-129">When the **ExactSpelling** field is **false**, as it is by default in C++ and C#, platform invoke searches for the mangled name first (**MessageBoxW**), then the unmangled alias (**MessageBox**) if the mangled name is not found.</span></span> <span data-ttu-id="faf88-130">Należy zauważyć, że zachowanie Dopasowywanie nazw Unicode różni się od zachowania Dopasowywanie nazw ANSI.</span><span class="sxs-lookup"><span data-stu-id="faf88-130">Notice that Unicode name-matching behavior differs from ANSI name-matching behavior.</span></span>  
  
 <span data-ttu-id="faf88-131">**CharSet.Auto**</span><span class="sxs-lookup"><span data-stu-id="faf88-131">**CharSet.Auto**</span></span>  
  
-   <span data-ttu-id="faf88-132">Wywołanie platformy wybiera między ANSI i Unicode formaty w czasie wykonywania, oparte na platformie docelowej.</span><span class="sxs-lookup"><span data-stu-id="faf88-132">Platform invoke chooses between ANSI and Unicode formats at run time, based on the target platform.</span></span>  
  
## <a name="specifying-a-character-set-in-visual-basic"></a><span data-ttu-id="faf88-133">Określanie zestawu znaków w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="faf88-133">Specifying a Character Set in Visual Basic</span></span>  
 <span data-ttu-id="faf88-134">Poniższy przykład deklaruje **MessageBox** funkcja trzy razy, każdorazowo przy użyciu różnych zachowanie zestawu znaków.</span><span class="sxs-lookup"><span data-stu-id="faf88-134">The following example declares the **MessageBox** function three times, each time with different character-set behavior.</span></span> <span data-ttu-id="faf88-135">Można określić zachowanie zestawu znaków w języku Visual Basic, dodając **Ansi**, **Unicode**, lub **automatycznie** — słowo kluczowe do instrukcji deklaracji.</span><span class="sxs-lookup"><span data-stu-id="faf88-135">You can specify character-set behavior in Visual Basic by adding the **Ansi**, **Unicode**, or **Auto** keyword to the declaration statement.</span></span>  
  
 <span data-ttu-id="faf88-136">Jeżeli pominięto słowa kluczowego zestaw znaków, jak odbywa się w pierwszej instrukcji deklaracji <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> pola wartość domyślna to zestawu znaków ANSI.</span><span class="sxs-lookup"><span data-stu-id="faf88-136">If you omit the character-set keyword, as is done in the first declaration statement, the <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field defaults to the ANSI character set.</span></span> <span data-ttu-id="faf88-137">Drugi i trzeci instrukcji w przykładzie jawnie określić znak, który został ustawiony za pomocą słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="faf88-137">The second and third statements in the example explicitly specify a character set with a keyword.</span></span>  
  
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
  
## <a name="specifying-a-character-set-in-c-and-c"></a><span data-ttu-id="faf88-138">Określanie zestawu znaków w C# i C++</span><span class="sxs-lookup"><span data-stu-id="faf88-138">Specifying a Character Set in C# and C++</span></span>  
 <span data-ttu-id="faf88-139"><xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> Pole identyfikuje podstawowy zestaw znaków jako ANSI lub Unicode.</span><span class="sxs-lookup"><span data-stu-id="faf88-139">The <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field identifies the underlying character set as ANSI or Unicode.</span></span> <span data-ttu-id="faf88-140">Formanty, jak powinny być wprowadzane argumenty typu string do metody zestawu znaków.</span><span class="sxs-lookup"><span data-stu-id="faf88-140">The character set controls how string arguments to a method should be marshaled.</span></span> <span data-ttu-id="faf88-141">Aby wskazać zestaw znaków, użyj jednej z następujących form:</span><span class="sxs-lookup"><span data-stu-id="faf88-141">Use one of the following forms to indicate the character set:</span></span>  
  
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
  
 <span data-ttu-id="faf88-142">W poniższym przykładzie przedstawiono trzy definicje zarządzanych **MessageBox** opartego na atrybutach funkcji do określenia zestawu znaków.</span><span class="sxs-lookup"><span data-stu-id="faf88-142">The following example shows three managed definitions of the **MessageBox** function attributed to specify a character set.</span></span> <span data-ttu-id="faf88-143">W pierwszym definicji przez jej pominięcia **CharSet** pola wartość domyślna to zestawu znaków ANSI.</span><span class="sxs-lookup"><span data-stu-id="faf88-143">In the first definition, by its omission, the **CharSet** field defaults to the ANSI character set.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="faf88-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="faf88-144">See also</span></span>
- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [<span data-ttu-id="faf88-145">Tworzenie prototypów w kodzie zarządzanym</span><span class="sxs-lookup"><span data-stu-id="faf88-145">Creating Prototypes in Managed Code</span></span>](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="faf88-146">Przykłady wywołań platformy</span><span class="sxs-lookup"><span data-stu-id="faf88-146">Platform Invoke Examples</span></span>](../../../docs/framework/interop/platform-invoke-examples.md)
- [<span data-ttu-id="faf88-147">Marshaling danych w wywołaniu platformy</span><span class="sxs-lookup"><span data-stu-id="faf88-147">Marshaling Data with Platform Invoke</span></span>](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)
