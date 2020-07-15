---
title: Określanie zestawu znaków
description: Dowiedz się, jak określić zestaw znaków, który używa kodowania z wąskim (ANSI) lub szerokim (Unicode). Możesz również określić wybór automatyczny środowiska uruchomieniowego.
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
ms.openlocfilehash: 789753742d8714e481f038e323407cbab0499f6c
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309797"
---
# <a name="specify-a-character-set"></a><span data-ttu-id="987f0-104">Określanie zestawu znaków</span><span class="sxs-lookup"><span data-stu-id="987f0-104">Specify a character set</span></span>

<span data-ttu-id="987f0-105"><xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType>Pole steruje kierowaniem ciągów i określa, w jaki sposób metoda Invoke odnajduje nazwy funkcji w bibliotece DLL.</span><span class="sxs-lookup"><span data-stu-id="987f0-105">The <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field controls string marshaling and determines how platform invoke finds function names in a DLL.</span></span> <span data-ttu-id="987f0-106">W tym temacie opisano oba zachowania.</span><span class="sxs-lookup"><span data-stu-id="987f0-106">This topic describes both behaviors.</span></span>  
  
 <span data-ttu-id="987f0-107">Niektóre interfejsy API eksportują dwie wersje funkcji przyjmujących argumenty ciągów: wąski (ANSI) i szeroki (Unicode).</span><span class="sxs-lookup"><span data-stu-id="987f0-107">Some APIs export two versions of functions that take string arguments: narrow (ANSI) and wide (Unicode).</span></span> <span data-ttu-id="987f0-108">Interfejs API systemu Windows, na przykład, zawiera następujące nazwy punktów wejścia dla funkcji **MessageBox** :</span><span class="sxs-lookup"><span data-stu-id="987f0-108">The Windows API, for instance, includes the following entry-point names for the **MessageBox** function:</span></span>  
  
- <span data-ttu-id="987f0-109">**MessageBoxA**</span><span class="sxs-lookup"><span data-stu-id="987f0-109">**MessageBoxA**</span></span>  
  
     <span data-ttu-id="987f0-110">Zawiera 1-bajtowe znaki formatowania ANSI, rozróżniane przez "A" do nazwy punktu wejścia.</span><span class="sxs-lookup"><span data-stu-id="987f0-110">Provides 1-byte character ANSI formatting, distinguished by an "A" appended to the entry-point name.</span></span> <span data-ttu-id="987f0-111">Wywołania klasy **MessageBox** są zawsze organizowane w formacie ANSI.</span><span class="sxs-lookup"><span data-stu-id="987f0-111">Calls to **MessageBoxA** always marshal strings in ANSI format.</span></span>  
  
- <span data-ttu-id="987f0-112">**MessageBoxW**</span><span class="sxs-lookup"><span data-stu-id="987f0-112">**MessageBoxW**</span></span>  
  
     <span data-ttu-id="987f0-113">Zawiera 2-bajtowe znaki formatowania Unicode, rozróżniane "W" dołączone do nazwy punktu wejścia.</span><span class="sxs-lookup"><span data-stu-id="987f0-113">Provides 2-byte character Unicode formatting, distinguished by a "W" appended to the entry-point name.</span></span> <span data-ttu-id="987f0-114">Wywołania **MessageBoxW** zawsze marshalą ciągi w formacie Unicode.</span><span class="sxs-lookup"><span data-stu-id="987f0-114">Calls to **MessageBoxW** always marshal strings in Unicode format.</span></span>  
  
## <a name="string-marshaling-and-name-matching"></a><span data-ttu-id="987f0-115">Kierowanie ciągów i dopasowywanie nazw</span><span class="sxs-lookup"><span data-stu-id="987f0-115">String Marshaling and Name Matching</span></span>  
 <span data-ttu-id="987f0-116">`CharSet`Pole akceptuje następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="987f0-116">The `CharSet` field accepts the following values:</span></span>  
  
 <span data-ttu-id="987f0-117"><xref:System.Runtime.InteropServices.CharSet.Ansi>(wartość domyślna)</span><span class="sxs-lookup"><span data-stu-id="987f0-117"><xref:System.Runtime.InteropServices.CharSet.Ansi> (default value)</span></span>  
  
- <span data-ttu-id="987f0-118">Kierowanie ciągów</span><span class="sxs-lookup"><span data-stu-id="987f0-118">String marshaling</span></span>  
  
     <span data-ttu-id="987f0-119">Wywołanie platformy umożliwia kierowanie ciągów z formatu zarządzanego (Unicode) do formatu ANSI.</span><span class="sxs-lookup"><span data-stu-id="987f0-119">Platform invoke marshals strings from their managed format (Unicode) to ANSI format.</span></span>  
  
- <span data-ttu-id="987f0-120">Dopasowanie nazw</span><span class="sxs-lookup"><span data-stu-id="987f0-120">Name matching</span></span>  
  
     <span data-ttu-id="987f0-121">Gdy <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType> pole ma `true` wartość domyślną w Visual Basic, platforma wywoła wyszukiwanie tylko dla określonej nazwy.</span><span class="sxs-lookup"><span data-stu-id="987f0-121">When the <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType> field is `true`, as it is by default in Visual Basic, platform invoke searches only for the name you specify.</span></span> <span data-ttu-id="987f0-122">Na przykład jeśli określisz element **MessageBox**, funkcja Invoke wywoła wyszukiwanie dla **MessageBox** i zakończy się niepowodzeniem, gdy nie będzie można zlokalizować dokładnej pisowni.</span><span class="sxs-lookup"><span data-stu-id="987f0-122">For example, if you specify **MessageBox**, platform invoke searches for **MessageBox** and fails when it cannot locate the exact spelling.</span></span>  
  
     <span data-ttu-id="987f0-123">Gdy `ExactSpelling` pole jest `false` , ponieważ jest domyślnie w języku C++ i C#, wywołanie platformy wyszuka alias niezniekształconej najpierw (**MessageBox**), a następnie nazwę zniekształcona (**MessageBox**), jeśli alias niezniekształconej nie zostanie znaleziony.</span><span class="sxs-lookup"><span data-stu-id="987f0-123">When the `ExactSpelling` field is `false`, as it is by default in C++ and C#, platform invoke searches for the unmangled alias first (**MessageBox**), then the mangled name (**MessageBoxA**) if the unmangled alias is not found.</span></span> <span data-ttu-id="987f0-124">Należy zauważyć, że zachowanie dopasowania nazw ANSI różni się od zachowania dopasowywania nazw Unicode.</span><span class="sxs-lookup"><span data-stu-id="987f0-124">Notice that ANSI name-matching behavior differs from Unicode name-matching behavior.</span></span>  
  
 <xref:System.Runtime.InteropServices.CharSet.Unicode>  
  
- <span data-ttu-id="987f0-125">Kierowanie ciągów</span><span class="sxs-lookup"><span data-stu-id="987f0-125">String marshaling</span></span>  
  
     <span data-ttu-id="987f0-126">Wywołanie platformy kopiuje ciągi z formatu zarządzanego (Unicode) do formatu Unicode.</span><span class="sxs-lookup"><span data-stu-id="987f0-126">Platform invoke copies strings from their managed format (Unicode) to Unicode format.</span></span>  
  
- <span data-ttu-id="987f0-127">Dopasowanie nazw</span><span class="sxs-lookup"><span data-stu-id="987f0-127">Name matching</span></span>  
  
     <span data-ttu-id="987f0-128">Gdy `ExactSpelling` pole ma `true` wartość domyślną w Visual Basic, platforma wywoła wyszukiwanie tylko dla określonej nazwy.</span><span class="sxs-lookup"><span data-stu-id="987f0-128">When the `ExactSpelling` field is `true`, as it is by default in Visual Basic, platform invoke searches only for the name you specify.</span></span> <span data-ttu-id="987f0-129">Na przykład jeśli określisz element **MessageBox**, funkcja Invoke wywoła wyszukiwanie dla **MessageBox** i zakończy się niepowodzeniem, jeśli nie można zlokalizować dokładnej pisowni.</span><span class="sxs-lookup"><span data-stu-id="987f0-129">For example, if you specify **MessageBox**, platform invoke searches for **MessageBox** and fails if it cannot locate the exact spelling.</span></span>  
  
     <span data-ttu-id="987f0-130">Gdy `ExactSpelling` pole jest `false` Domyślnie w języku C++ i C#, wywołanie platformy wyszukuje najpierw nazwę zniekształcona (**MessageBoxW**), a następnie alias niezniekształconej (**MessageBox**), jeśli nie odnaleziono nazwy zniekształcona.</span><span class="sxs-lookup"><span data-stu-id="987f0-130">When the `ExactSpelling` field is `false`, as it is by default in C++ and C#, platform invoke searches for the mangled name first (**MessageBoxW**), then the unmangled alias (**MessageBox**) if the mangled name is not found.</span></span> <span data-ttu-id="987f0-131">Zauważ, że zachowanie dopasowywania nazw Unicode różni się od zachowania dopasowania nazw ANSI.</span><span class="sxs-lookup"><span data-stu-id="987f0-131">Notice that Unicode name-matching behavior differs from ANSI name-matching behavior.</span></span>  
  
 <xref:System.Runtime.InteropServices.CharSet.Auto>  
  
- <span data-ttu-id="987f0-132">Wywołanie platformy wybiera między formatami ANSI i Unicode w czasie wykonywania, na podstawie platformy docelowej.</span><span class="sxs-lookup"><span data-stu-id="987f0-132">Platform invoke chooses between ANSI and Unicode formats at run time, based on the target platform.</span></span>  
  
## <a name="specify-a-character-set-in-visual-basic"></a><span data-ttu-id="987f0-133">Określ zestaw znaków w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="987f0-133">Specify a character set in Visual Basic</span></span>

<span data-ttu-id="987f0-134">Możesz określić zachowanie zestawu znaków w Visual Basic, dodając `Ansi` `Unicode` słowo kluczowe,, lub `Auto` do instrukcji deklaracji.</span><span class="sxs-lookup"><span data-stu-id="987f0-134">You can specify character-set behavior in Visual Basic by adding the `Ansi`, `Unicode`, or `Auto` keyword to the declaration statement.</span></span> <span data-ttu-id="987f0-135">W przypadku pominięcia słowa kluczowego zestawu znaków <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> wartością domyślną pola jest zestaw znaków ANSI.</span><span class="sxs-lookup"><span data-stu-id="987f0-135">If you omit the character-set keyword, the <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field defaults to the ANSI character set.</span></span>

<span data-ttu-id="987f0-136">Poniższy przykład deklaruje funkcję **MessageBox** trzykrotnie, za każdym razem z innym zachowaniem zestawu znaków.</span><span class="sxs-lookup"><span data-stu-id="987f0-136">The following example declares the **MessageBox** function three times, each time with different character-set behavior.</span></span> <span data-ttu-id="987f0-137">Pierwsza instrukcja pomija słowo kluczowe zestawu znaków, dlatego zestaw znaków jest domyślnie ANSI.</span><span class="sxs-lookup"><span data-stu-id="987f0-137">The first statement omits the character-set keyword, so the character set defaults to ANSI.</span></span> <span data-ttu-id="987f0-138">Drugie i trzecie instrukcje jawnie określają zestaw znaków za pomocą słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="987f0-138">The second and third statements explicitly specify a character set with a keyword.</span></span>

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
  
## <a name="specify-a-character-set-in-c-and-c"></a><span data-ttu-id="987f0-139">Określanie zestawu znaków w językach C# i C++</span><span class="sxs-lookup"><span data-stu-id="987f0-139">Specify a character set in C# and C++</span></span>

<span data-ttu-id="987f0-140"><xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType>Pole Identyfikuje podstawowy zestaw znaków jako ANSI lub Unicode.</span><span class="sxs-lookup"><span data-stu-id="987f0-140">The <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field identifies the underlying character set as ANSI or Unicode.</span></span> <span data-ttu-id="987f0-141">Zestaw znaków kontroluje sposób organizowania argumentów ciągów dla metody.</span><span class="sxs-lookup"><span data-stu-id="987f0-141">The character set controls how string arguments to a method should be marshaled.</span></span> <span data-ttu-id="987f0-142">Aby wskazać zestaw znaków, użyj jednej z następujących form:</span><span class="sxs-lookup"><span data-stu-id="987f0-142">Use one of the following forms to indicate the character set:</span></span>  
  
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
  
 <span data-ttu-id="987f0-143">W poniższym przykładzie przedstawiono trzy zarządzane definicje funkcji **MessageBox** przypisanej do określenia zestawu znaków.</span><span class="sxs-lookup"><span data-stu-id="987f0-143">The following example shows three managed definitions of the **MessageBox** function attributed to specify a character set.</span></span> <span data-ttu-id="987f0-144">W pierwszej definicji, z pominięciem, `CharSet` pole domyślnie jest zestaw znaków ANSI.</span><span class="sxs-lookup"><span data-stu-id="987f0-144">In the first definition, by its omission, the `CharSet` field defaults to the ANSI character set.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="987f0-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="987f0-145">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [<span data-ttu-id="987f0-146">Tworzenie prototypów w kodzie zarządzanym</span><span class="sxs-lookup"><span data-stu-id="987f0-146">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="987f0-147">Przykłady wywołań platformy</span><span class="sxs-lookup"><span data-stu-id="987f0-147">Platform Invoke Examples</span></span>](platform-invoke-examples.md)
- [<span data-ttu-id="987f0-148">Organizowanie danych w wywołaniu platformy</span><span class="sxs-lookup"><span data-stu-id="987f0-148">Marshaling Data with Platform Invoke</span></span>](marshaling-data-with-platform-invoke.md)
