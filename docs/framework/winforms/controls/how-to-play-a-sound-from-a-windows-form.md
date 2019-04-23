---
title: 'Instrukcje: odtwarzanie dźwięku za pomocą formularza systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- playing sounds [Windows Forms], Windows Forms
- sounds [Windows Forms], playing
- sounds
- My.Computer.Audio object [Windows Forms], playing sounds
- examples [Windows Forms], sounds
ms.assetid: 3d3350b7-1ebd-4e05-a738-48ca1160a19d
ms.openlocfilehash: 3b9eb6f902d0d2193f0099f8e868e4ead347ce26
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59078684"
---
# <a name="how-to-play-a-sound-from-a-windows-form"></a><span data-ttu-id="81b4b-102">Instrukcje: odtwarzanie dźwięku za pomocą formularza systemu Windows</span><span class="sxs-lookup"><span data-stu-id="81b4b-102">How to: Play a Sound from a Windows Form</span></span>
<span data-ttu-id="81b4b-103">W tym przykładzie odtwarza dźwięk w danej ścieżce w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="81b4b-103">This example plays a sound at a given path at run time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="81b4b-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="81b4b-104">Example</span></span>  
  
```vb  
Sub PlaySimpleSound()  
    My.Computer.Audio.Play("c:\Windows\Media\chimes.wav")  
End Sub  
```  
  
```csharp  
private void playSimpleSound()  
{  
    SoundPlayer simpleSound = new SoundPlayer(@"c:\Windows\Media\chimes.wav");  
    simpleSound.Play();  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="81b4b-105">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="81b4b-105">Compiling the Code</span></span>  
 <span data-ttu-id="81b4b-106">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="81b4b-106">This example requires:</span></span>  
  
-   <span data-ttu-id="81b4b-107">Zastąp nazwę pliku `"c:\Windows\Media\chimes.wav"` z prawidłową nazwą pliku.</span><span class="sxs-lookup"><span data-stu-id="81b4b-107">That you replace the file name `"c:\Windows\Media\chimes.wav"` with a valid file name.</span></span>  
  
-   <span data-ttu-id="81b4b-108">(C#) Odwołanie do <xref:System.Media?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="81b4b-108">(C#) A reference to the <xref:System.Media?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="81b4b-109">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="81b4b-109">Robust Programming</span></span>  
 <span data-ttu-id="81b4b-110">Operacje na plikach powinna zostać ujęta w odpowiednie bloki obsługi wyjątków strukturalnych.</span><span class="sxs-lookup"><span data-stu-id="81b4b-110">File operations should be enclosed within appropriate structured exception handling blocks.</span></span>  
  
 <span data-ttu-id="81b4b-111">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="81b4b-111">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="81b4b-112">Nazwa ścieżki jest nieprawidłowo sformułowany.</span><span class="sxs-lookup"><span data-stu-id="81b4b-112">The path name is malformed.</span></span> <span data-ttu-id="81b4b-113">Na przykład zawiera niedozwolone znaki lub jest tylko spacją (<xref:System.ArgumentException> klasy).</span><span class="sxs-lookup"><span data-stu-id="81b4b-113">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException> class).</span></span>  
  
-   <span data-ttu-id="81b4b-114">Ścieżka jest tylko do odczytu (<xref:System.IO.IOException> klasy).</span><span class="sxs-lookup"><span data-stu-id="81b4b-114">The path is read-only (<xref:System.IO.IOException> class).</span></span>  
  
-   <span data-ttu-id="81b4b-115">Nazwa ścieżki jest `null` (<xref:System.ArgumentNullException> klasy).</span><span class="sxs-lookup"><span data-stu-id="81b4b-115">The path name is `null` (<xref:System.ArgumentNullException> class).</span></span>  
  
-   <span data-ttu-id="81b4b-116">Nazwa ścieżki jest za długa (<xref:System.IO.PathTooLongException> klasy).</span><span class="sxs-lookup"><span data-stu-id="81b4b-116">The path name is too long (<xref:System.IO.PathTooLongException> class).</span></span>  
  
-   <span data-ttu-id="81b4b-117">Ścieżka jest nieprawidłowa (<xref:System.IO.DirectoryNotFoundException> klasy).</span><span class="sxs-lookup"><span data-stu-id="81b4b-117">The path is invalid (<xref:System.IO.DirectoryNotFoundException> class).</span></span>  
  
-   <span data-ttu-id="81b4b-118">Ścieżka jest tylko dwukropek, ":" (<xref:System.NotSupportedException> klasy).</span><span class="sxs-lookup"><span data-stu-id="81b4b-118">The path is only a colon, ":" (<xref:System.NotSupportedException> class).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="81b4b-119">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="81b4b-119">.NET Framework Security</span></span>  
 <span data-ttu-id="81b4b-120">Nie należy podejmować decyzji dotyczących zawartości pliku na podstawie rozszerzenia nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="81b4b-120">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="81b4b-121">Na przykład plik `Form1.vb` może nie być plikiem źródłowym programu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="81b4b-121">For example, the file `Form1.vb` may not be a Visual Basic source file.</span></span> <span data-ttu-id="81b4b-122">Sprawdź wszystkie dane wejściowe, zanim użyjesz danych w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="81b4b-122">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81b4b-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="81b4b-123">See also</span></span>

- <xref:System.Media.SoundPlayer>
- [<span data-ttu-id="81b4b-124">Instrukcje: Ładowanie dźwięku asynchronicznie w formularzu Windows</span><span class="sxs-lookup"><span data-stu-id="81b4b-124">How to: Load a Sound Asynchronously within a Windows Form</span></span>](how-to-load-a-sound-asynchronously-within-a-windows-form.md)
