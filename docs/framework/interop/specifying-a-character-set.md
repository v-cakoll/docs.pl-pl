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
ms.openlocfilehash: 9ee68d0da3b7f23d4de0192da076ef6f71d6d222
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71051633"
---
# <a name="specifying-a-character-set"></a><span data-ttu-id="1ef0f-102">Określanie zestawu znaków</span><span class="sxs-lookup"><span data-stu-id="1ef0f-102">Specifying a Character Set</span></span>
<span data-ttu-id="1ef0f-103"><xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> Pole steruje kierowaniem ciągów i określa, w jaki sposób metoda Invoke odnajduje nazwy funkcji w bibliotece DLL.</span><span class="sxs-lookup"><span data-stu-id="1ef0f-103">The <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field controls string marshaling and determines how platform invoke finds function names in a DLL.</span></span> <span data-ttu-id="1ef0f-104">W tym temacie opisano oba zachowania.</span><span class="sxs-lookup"><span data-stu-id="1ef0f-104">This topic describes both behaviors.</span></span>  
  
 <span data-ttu-id="1ef0f-105">Niektóre interfejsy API eksportują dwie wersje funkcji przyjmujących argumenty ciągów: wąski (ANSI) i szeroki (Unicode).</span><span class="sxs-lookup"><span data-stu-id="1ef0f-105">Some APIs export two versions of functions that take string arguments: narrow (ANSI) and wide (Unicode).</span></span> <span data-ttu-id="1ef0f-106">Interfejs API systemu Windows, na przykład, zawiera następujące nazwy punktów wejścia dla funkcji **MessageBox** :</span><span class="sxs-lookup"><span data-stu-id="1ef0f-106">The Windows API, for instance, includes the following entry-point names for the **MessageBox** function:</span></span>  
  
- <span data-ttu-id="1ef0f-107">**MessageBoxA**</span><span class="sxs-lookup"><span data-stu-id="1ef0f-107">**MessageBoxA**</span></span>  
  
     <span data-ttu-id="1ef0f-108">Zawiera 1-bajtowe znaki formatowania ANSI, rozróżniane przez "A" do nazwy punktu wejścia.</span><span class="sxs-lookup"><span data-stu-id="1ef0f-108">Provides 1-byte character ANSI formatting, distinguished by an "A" appended to the entry-point name.</span></span> <span data-ttu-id="1ef0f-109">Wywołania klasy **MessageBox** są zawsze organizowane w formacie ANSI.</span><span class="sxs-lookup"><span data-stu-id="1ef0f-109">Calls to **MessageBoxA** always marshal strings in ANSI format.</span></span>  
  
- <span data-ttu-id="1ef0f-110">**MessageBoxW**</span><span class="sxs-lookup"><span data-stu-id="1ef0f-110">**MessageBoxW**</span></span>  
  
     <span data-ttu-id="1ef0f-111">Zawiera 2-bajtowe znaki formatowania Unicode, rozróżniane "W" dołączone do nazwy punktu wejścia.</span><span class="sxs-lookup"><span data-stu-id="1ef0f-111">Provides 2-byte character Unicode formatting, distinguished by a "W" appended to the entry-point name.</span></span> <span data-ttu-id="1ef0f-112">Wywołania **MessageBoxW** zawsze marshalą ciągi w formacie Unicode.</span><span class="sxs-lookup"><span data-stu-id="1ef0f-112">Calls to **MessageBoxW** always marshal strings in Unicode format.</span></span>  
  
## <a name="string-marshaling-and-name-matching"></a><span data-ttu-id="1ef0f-113">Kierowanie ciągów i dopasowywanie nazw</span><span class="sxs-lookup"><span data-stu-id="1ef0f-113">String Marshaling and Name Matching</span></span>  
 <span data-ttu-id="1ef0f-114">`CharSet` Pole akceptuje następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="1ef0f-114">The `CharSet` field accepts the following values:</span></span>  
  
 <span data-ttu-id="1ef0f-115"><xref:System.Runtime.InteropServices.CharSet.Ansi>(wartość domyślna)</span><span class="sxs-lookup"><span data-stu-id="1ef0f-115"><xref:System.Runtime.InteropServices.CharSet.Ansi> (default value)</span></span>  
  
- <span data-ttu-id="1ef0f-116">Kierowanie ciągów</span><span class="sxs-lookup"><span data-stu-id="1ef0f-116">String marshaling</span></span>  
  
     <span data-ttu-id="1ef0f-117">Wywołanie platformy umożliwia kierowanie ciągów z formatu zarządzanego (Unicode) do formatu ANSI.</span><span class="sxs-lookup"><span data-stu-id="1ef0f-117">Platform invoke marshals strings from their managed format (Unicode) to ANSI format.</span></span>  
  
- <span data-ttu-id="1ef0f-118">Dopasowanie nazw</span><span class="sxs-lookup"><span data-stu-id="1ef0f-118">Name matching</span></span>  
  
     <span data-ttu-id="1ef0f-119">Gdy pole ma `true`wartość domyślną w Visual Basic, platforma wywoła wyszukiwanie tylko dla określonej nazwy. <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="1ef0f-119">When the <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType> field is `true`, as it is by default in Visual Basic, platform invoke searches only for the name you specify.</span></span> <span data-ttu-id="1ef0f-120">Na przykład jeśli określisz element **MessageBox**, funkcja Invoke wywoła wyszukiwanie dla **MessageBox** i zakończy się niepowodzeniem, gdy nie będzie można zlokalizować dokładnej pisowni.</span><span class="sxs-lookup"><span data-stu-id="1ef0f-120">For example, if you specify **MessageBox**, platform invoke searches for **MessageBox** and fails when it cannot locate the exact spelling.</span></span>  
  
     <span data-ttu-id="1ef0f-121">`false` C++ C#Gdy pole jest, ponieważ jest domyślnie w i, wywołanie platformy wyszuka alias niezniekształconej najpierw (MessageBox), a następnie nazwę zniekształcona (MessageBox), jeśli alias niezniekształconej nie zostanie znaleziony. `ExactSpelling`</span><span class="sxs-lookup"><span data-stu-id="1ef0f-121">When the `ExactSpelling` field is `false`, as it is by default in C++ and C#, platform invoke searches for the unmangled alias first (**MessageBox**), then the mangled name (**MessageBoxA**) if the unmangled alias is not found.</span></span> <span data-ttu-id="1ef0f-122">Należy zauważyć, że zachowanie dopasowania nazw ANSI różni się od zachowania dopasowywania nazw Unicode.</span><span class="sxs-lookup"><span data-stu-id="1ef0f-122">Notice that ANSI name-matching behavior differs from Unicode name-matching behavior.</span></span>  
  
 <xref:System.Runtime.InteropServices.CharSet.Unicode>  
  
- <span data-ttu-id="1ef0f-123">Kierowanie ciągów</span><span class="sxs-lookup"><span data-stu-id="1ef0f-123">String marshaling</span></span>  
  
     <span data-ttu-id="1ef0f-124">Wywołanie platformy kopiuje ciągi z formatu zarządzanego (Unicode) do formatu Unicode.</span><span class="sxs-lookup"><span data-stu-id="1ef0f-124">Platform invoke copies strings from their managed format (Unicode) to Unicode format.</span></span>  
  
- <span data-ttu-id="1ef0f-125">Dopasowanie nazw</span><span class="sxs-lookup"><span data-stu-id="1ef0f-125">Name matching</span></span>  
  
     <span data-ttu-id="1ef0f-126">Gdy pole ma `true`wartość domyślną w Visual Basic, platforma wywoła wyszukiwanie tylko dla określonej nazwy. `ExactSpelling`</span><span class="sxs-lookup"><span data-stu-id="1ef0f-126">When the `ExactSpelling` field is `true`, as it is by default in Visual Basic, platform invoke searches only for the name you specify.</span></span> <span data-ttu-id="1ef0f-127">Na przykład jeśli określisz element **MessageBox**, funkcja Invoke wywoła wyszukiwanie dla **MessageBox** i zakończy się niepowodzeniem, jeśli nie można zlokalizować dokładnej pisowni.</span><span class="sxs-lookup"><span data-stu-id="1ef0f-127">For example, if you specify **MessageBox**, platform invoke searches for **MessageBox** and fails if it cannot locate the exact spelling.</span></span>  
  
     <span data-ttu-id="1ef0f-128">`false` C++ C#Gdy pole jest, ponieważ jest domyślnie w i, wywołanie platformy wyszukuje najpierw nazwę zniekształcona (MessageBoxW), a następnie alias niezniekształconej (MessageBox), jeśli nazwa zniekształcona nie zostanie znaleziona. `ExactSpelling`</span><span class="sxs-lookup"><span data-stu-id="1ef0f-128">When the `ExactSpelling` field is `false`, as it is by default in C++ and C#, platform invoke searches for the mangled name first (**MessageBoxW**), then the unmangled alias (**MessageBox**) if the mangled name is not found.</span></span> <span data-ttu-id="1ef0f-129">Zauważ, że zachowanie dopasowywania nazw Unicode różni się od zachowania dopasowania nazw ANSI.</span><span class="sxs-lookup"><span data-stu-id="1ef0f-129">Notice that Unicode name-matching behavior differs from ANSI name-matching behavior.</span></span>  
  
 <xref:System.Runtime.InteropServices.CharSet.Auto>  
  
- <span data-ttu-id="1ef0f-130">Wywołanie platformy wybiera między formatami ANSI i Unicode w czasie wykonywania, na podstawie platformy docelowej.</span><span class="sxs-lookup"><span data-stu-id="1ef0f-130">Platform invoke chooses between ANSI and Unicode formats at run time, based on the target platform.</span></span>  
  
## <a name="specifying-a-character-set-in-visual-basic"></a><span data-ttu-id="1ef0f-131">Określanie zestawu znaków w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1ef0f-131">Specifying a Character Set in Visual Basic</span></span>  
 <span data-ttu-id="1ef0f-132">Poniższy przykład deklaruje funkcję **MessageBox** trzykrotnie, za każdym razem z innym zachowaniem zestawu znaków.</span><span class="sxs-lookup"><span data-stu-id="1ef0f-132">The following example declares the **MessageBox** function three times, each time with different character-set behavior.</span></span> <span data-ttu-id="1ef0f-133">Możesz określić zachowanie zestawu znaków w Visual Basic, dodając słowo kluczowe **ANSI**, **Unicode**lub słowa kluczowego do instrukcji deklaracji.</span><span class="sxs-lookup"><span data-stu-id="1ef0f-133">You can specify character-set behavior in Visual Basic by adding the **Ansi**, **Unicode**, or **Auto** keyword to the declaration statement.</span></span>  
  
 <span data-ttu-id="1ef0f-134">W przypadku pominięcia słowa kluczowego zestawu znaków, jak zostało to zrobione w pierwszej instrukcji deklaracji <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> , pole jest domyślnie ustawione na zestaw znaków ANSI.</span><span class="sxs-lookup"><span data-stu-id="1ef0f-134">If you omit the character-set keyword, as is done in the first declaration statement, the <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field defaults to the ANSI character set.</span></span> <span data-ttu-id="1ef0f-135">Drugie i trzecie instrukcje w przykładzie jawnie określają zestaw znaków za pomocą słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="1ef0f-135">The second and third statements in the example explicitly specify a character set with a keyword.</span></span>  
  
```vb
Friend Class NativeMethods
    Friend Declare Function MessageBoxA Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer

    Friend Declare Unicode Function MessageBoxW Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer

    Friend Declare Auto Function MessageBox Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
End Class
```
  
## <a name="specifying-a-character-set-in-c-and-c"></a><span data-ttu-id="1ef0f-136">Określanie zestawu znaków w C# iC++</span><span class="sxs-lookup"><span data-stu-id="1ef0f-136">Specifying a Character Set in C# and C++</span></span>  
 <span data-ttu-id="1ef0f-137"><xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> Pole Identyfikuje podstawowy zestaw znaków jako ANSI lub Unicode.</span><span class="sxs-lookup"><span data-stu-id="1ef0f-137">The <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field identifies the underlying character set as ANSI or Unicode.</span></span> <span data-ttu-id="1ef0f-138">Zestaw znaków kontroluje sposób organizowania argumentów ciągów dla metody.</span><span class="sxs-lookup"><span data-stu-id="1ef0f-138">The character set controls how string arguments to a method should be marshaled.</span></span> <span data-ttu-id="1ef0f-139">Aby wskazać zestaw znaków, użyj jednej z następujących form:</span><span class="sxs-lookup"><span data-stu-id="1ef0f-139">Use one of the following forms to indicate the character set:</span></span>  
  
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
  
 <span data-ttu-id="1ef0f-140">W poniższym przykładzie przedstawiono trzy zarządzane definicje funkcji **MessageBox** przypisanej do określenia zestawu znaków.</span><span class="sxs-lookup"><span data-stu-id="1ef0f-140">The following example shows three managed definitions of the **MessageBox** function attributed to specify a character set.</span></span> <span data-ttu-id="1ef0f-141">W pierwszej definicji, z pominięciem, pole domyślnie `CharSet` jest zestaw znaków ANSI.</span><span class="sxs-lookup"><span data-stu-id="1ef0f-141">In the first definition, by its omission, the `CharSet` field defaults to the ANSI character set.</span></span>  
  
```csharp  
using System;
using System.Runtime.InteropServices;

internal static class NativeMethods
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
  
## <a name="see-also"></a><span data-ttu-id="1ef0f-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1ef0f-142">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [<span data-ttu-id="1ef0f-143">Tworzenie prototypów w kodzie zarządzanym</span><span class="sxs-lookup"><span data-stu-id="1ef0f-143">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="1ef0f-144">Przykłady wywołań platformy</span><span class="sxs-lookup"><span data-stu-id="1ef0f-144">Platform Invoke Examples</span></span>](platform-invoke-examples.md)
- [<span data-ttu-id="1ef0f-145">Marshaling danych w wywołaniu platformy</span><span class="sxs-lookup"><span data-stu-id="1ef0f-145">Marshaling Data with Platform Invoke</span></span>](marshaling-data-with-platform-invoke.md)
