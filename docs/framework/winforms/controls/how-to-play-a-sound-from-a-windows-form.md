---
title: 'Porady: odtwarzanie dźwięku za pomocą formularza systemu Windows'
description: Dowiedz się, jak odtworzyć dźwięk z formularza systemu Windows w danej ścieżce w czasie wykonywania. Dowiedz się również, jak skompilować kod i strukturę zabezpieczeń .NET.
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
ms.openlocfilehash: beb17d994e224f41b2b590ecb1401988cdad314d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85613751"
---
# <a name="how-to-play-a-sound-from-a-windows-form"></a><span data-ttu-id="b4bbd-104">Porady: odtwarzanie dźwięku za pomocą formularza systemu Windows</span><span class="sxs-lookup"><span data-stu-id="b4bbd-104">How to: Play a Sound from a Windows Form</span></span>
<span data-ttu-id="b4bbd-105">Ten przykład odtwarza dźwięk w danej ścieżce w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="b4bbd-105">This example plays a sound at a given path at run time.</span></span>

## <a name="example"></a><span data-ttu-id="b4bbd-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="b4bbd-106">Example</span></span>

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

## <a name="compiling-the-code"></a><span data-ttu-id="b4bbd-107">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="b4bbd-107">Compiling the Code</span></span>
 <span data-ttu-id="b4bbd-108">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="b4bbd-108">This example requires:</span></span>

- <span data-ttu-id="b4bbd-109">Zastąp nazwę pliku `"c:\Windows\Media\chimes.wav"` prawidłową nazwą pliku.</span><span class="sxs-lookup"><span data-stu-id="b4bbd-109">That you replace the file name `"c:\Windows\Media\chimes.wav"` with a valid file name.</span></span>

- <span data-ttu-id="b4bbd-110">Znajd Odwołanie do <xref:System.Media?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="b4bbd-110">(C#) A reference to the <xref:System.Media?displayProperty=nameWithType> namespace.</span></span>

## <a name="robust-programming"></a><span data-ttu-id="b4bbd-111">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="b4bbd-111">Robust Programming</span></span>
 <span data-ttu-id="b4bbd-112">Operacje na plikach powinny być ujęte w obrębie odpowiednich bloków obsługi wyjątków strukturalnych.</span><span class="sxs-lookup"><span data-stu-id="b4bbd-112">File operations should be enclosed within appropriate structured exception handling blocks.</span></span>

 <span data-ttu-id="b4bbd-113">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="b4bbd-113">The following conditions may cause an exception:</span></span>

- <span data-ttu-id="b4bbd-114">Nazwa ścieżki jest źle sformułowana.</span><span class="sxs-lookup"><span data-stu-id="b4bbd-114">The path name is malformed.</span></span> <span data-ttu-id="b4bbd-115">Na przykład zawiera niedozwolone znaki lub jest tylko białym znakiem ( <xref:System.ArgumentException> Klasa).</span><span class="sxs-lookup"><span data-stu-id="b4bbd-115">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException> class).</span></span>

- <span data-ttu-id="b4bbd-116">Ścieżka jest tylko do odczytu ( <xref:System.IO.IOException> Klasa).</span><span class="sxs-lookup"><span data-stu-id="b4bbd-116">The path is read-only (<xref:System.IO.IOException> class).</span></span>

- <span data-ttu-id="b4bbd-117">Nazwa ścieżki to `null` ( <xref:System.ArgumentNullException> Klasa).</span><span class="sxs-lookup"><span data-stu-id="b4bbd-117">The path name is `null` (<xref:System.ArgumentNullException> class).</span></span>

- <span data-ttu-id="b4bbd-118">Nazwa ścieżki jest za długa ( <xref:System.IO.PathTooLongException> Klasa).</span><span class="sxs-lookup"><span data-stu-id="b4bbd-118">The path name is too long (<xref:System.IO.PathTooLongException> class).</span></span>

- <span data-ttu-id="b4bbd-119">Ścieżka jest nieprawidłowa ( <xref:System.IO.DirectoryNotFoundException> Klasa).</span><span class="sxs-lookup"><span data-stu-id="b4bbd-119">The path is invalid (<xref:System.IO.DirectoryNotFoundException> class).</span></span>

- <span data-ttu-id="b4bbd-120">Ścieżka ma tylko dwukropek, ":" ( <xref:System.NotSupportedException> Klasa).</span><span class="sxs-lookup"><span data-stu-id="b4bbd-120">The path is only a colon, ":" (<xref:System.NotSupportedException> class).</span></span>

## <a name="net-framework-security"></a><span data-ttu-id="b4bbd-121">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="b4bbd-121">.NET Framework Security</span></span>
 <span data-ttu-id="b4bbd-122">Nie należy podejmować decyzji dotyczących zawartości pliku na podstawie rozszerzenia nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="b4bbd-122">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="b4bbd-123">Na przykład plik `Form1.vb` nie może być plikiem źródłowym Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b4bbd-123">For example, the file `Form1.vb` may not be a Visual Basic source file.</span></span> <span data-ttu-id="b4bbd-124">Sprawdź wszystkie dane wejściowe, zanim użyjesz danych w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b4bbd-124">Verify all inputs before using the data in your application.</span></span>

## <a name="see-also"></a><span data-ttu-id="b4bbd-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b4bbd-125">See also</span></span>

- <xref:System.Media.SoundPlayer>
- [<span data-ttu-id="b4bbd-126">Instrukcje: ładowanie dźwięku asynchronicznie w formularzu systemu Windows</span><span class="sxs-lookup"><span data-stu-id="b4bbd-126">How to: Load a Sound Asynchronously within a Windows Form</span></span>](how-to-load-a-sound-asynchronously-within-a-windows-form.md)
