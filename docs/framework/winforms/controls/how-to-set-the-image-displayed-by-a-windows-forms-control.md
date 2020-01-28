---
title: Ustawianie obrazu wyświetlanego przez kontrolkę
ms.date: 08/20/2019
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Button control [Windows Forms], images
- Windows Forms controls, images
- controls [Windows Forms], images
- images [Windows Forms], Windows Forms controls
- examples [Windows Forms], controls
ms.assetid: 9445af8f-4f62-48b0-a3f6-068058964b9f
ms.openlocfilehash: 5df0068c8462bbaab0cb0135de1dd1b91ababe06
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746872"
---
# <a name="how-to-set-the-image-displayed-by-a-windows-forms-control"></a><span data-ttu-id="c42dc-102">Instrukcje: Ustawianie obrazu wyświetlanego przez kontrolkę Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c42dc-102">How to: Set the image displayed by a Windows Forms control</span></span>

<span data-ttu-id="c42dc-103">Kilka kontrolek Windows Forms może wyświetlać obrazy.</span><span class="sxs-lookup"><span data-stu-id="c42dc-103">Several Windows Forms controls can display images.</span></span> <span data-ttu-id="c42dc-104">Te obrazy mogą być ikonami, które wyjaśniają przeznaczenie kontrolki, na przykład ikona dyskietki na przycisku oznaczającego polecenie Zapisz.</span><span class="sxs-lookup"><span data-stu-id="c42dc-104">These images can be icons that clarify the purpose of the control, such as a diskette icon on a button denoting the Save command.</span></span> <span data-ttu-id="c42dc-105">Alternatywnie, ikony mogą być obrazami tła, aby nadać formantowi wygląd i zachowanie.</span><span class="sxs-lookup"><span data-stu-id="c42dc-105">Alternatively, the icons can be background images to give the control the appearance and behavior you want.</span></span>

## <a name="programmatic"></a><span data-ttu-id="c42dc-106">Program</span><span class="sxs-lookup"><span data-stu-id="c42dc-106">Programmatic</span></span>

<span data-ttu-id="c42dc-107">Ustaw właściwość `Image` lub `BackgroundImage` kontrolki na obiekt typu <xref:System.Drawing.Image>.</span><span class="sxs-lookup"><span data-stu-id="c42dc-107">Set the control's `Image` or `BackgroundImage` property to an object of type <xref:System.Drawing.Image>.</span></span> <span data-ttu-id="c42dc-108">Ogólnie rzecz biorąc, zostanie załadowany obraz z pliku za pomocą metody <xref:System.Drawing.Image.FromFile%2A>.</span><span class="sxs-lookup"><span data-stu-id="c42dc-108">Generally, you'll be loading the image from a file by using the <xref:System.Drawing.Image.FromFile%2A> method.</span></span>

<span data-ttu-id="c42dc-109">W poniższym przykładzie kodu ścieżka ustawiona dla lokalizacji obrazu jest folderem **Moje obrazy** .</span><span class="sxs-lookup"><span data-stu-id="c42dc-109">In the following code example, the path set for the location of the image is the **My Pictures** folder.</span></span> <span data-ttu-id="c42dc-110">Większość komputerów z systemem operacyjnym Windows zawiera ten katalog.</span><span class="sxs-lookup"><span data-stu-id="c42dc-110">Most computers running the Windows operating system include this directory.</span></span> <span data-ttu-id="c42dc-111">Dzięki temu użytkownicy mający minimalne poziomy dostępu do systemu mogą bezpiecznie uruchamiać aplikację.</span><span class="sxs-lookup"><span data-stu-id="c42dc-111">This also enables users with minimal system access levels to run the application safely.</span></span> <span data-ttu-id="c42dc-112">Poniższy przykład kodu wymaga już formularza z dodaną kontrolką <xref:System.Windows.Forms.PictureBox>.</span><span class="sxs-lookup"><span data-stu-id="c42dc-112">The following code example requires that you already have a form with a <xref:System.Windows.Forms.PictureBox> control added.</span></span>

```vb
' Replace the image named below with your own icon.
PictureBox1.Image = Image.FromFile _
   (System.Environment.GetFolderPath _
   (System.Environment.SpecialFolder.MyPictures) _
   & "\Image.gif")
```

```csharp
// Replace the image named below with your own icon.
// Note the escape character used (@) when specifying the path.
pictureBox1.Image = Image.FromFile
   (System.Environment.GetFolderPath
   (System.Environment.SpecialFolder.MyPictures)
   + @"\Image.gif");
```

```cpp
// Replace the image named below with your own icon.
pictureBox1->Image = Image::FromFile(String::Concat
   (System::Environment::GetFolderPath
   (System::Environment::SpecialFolder::MyPictures),
   "\\Image.gif"));
```

## <a name="designer"></a><span data-ttu-id="c42dc-113">Designer</span><span class="sxs-lookup"><span data-stu-id="c42dc-113">Designer</span></span>

1. <span data-ttu-id="c42dc-114">W oknie **Właściwości** programu Visual Studio zaznacz właściwość **obraz** lub **BackgroundImage** kontrolki, a następnie wybierz przycisk wielokropka (![symbol wielokropka w programie Visual Studio](./media/visual-studio-ellipsis-button.png)), aby wyświetlić okno dialogowe **Wybieranie zasobu** .</span><span class="sxs-lookup"><span data-stu-id="c42dc-114">In the **Properties** window of Visual Studio, select the **Image** or **BackgroundImage** property of the control, and then select the ellipsis (![Ellipsis button in Visual Studio](./media/visual-studio-ellipsis-button.png)) to display the **Select Resource** dialog box.</span></span>

2. <span data-ttu-id="c42dc-115">Wybierz obraz, który chcesz wyświetlić.</span><span class="sxs-lookup"><span data-stu-id="c42dc-115">Select the image you want to display.</span></span>

## <a name="see-also"></a><span data-ttu-id="c42dc-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c42dc-116">See also</span></span>

- <xref:System.Drawing.Image.FromFile%2A>
- <xref:System.Drawing.Image>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
