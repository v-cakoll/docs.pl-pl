---
title: 'Instrukcje: ustawianie obrazu wyświetlanego przez kontrolkę formularzy systemu Windows'
ms.date: 03/30/2017
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
ms.openlocfilehash: 99bde4fac7b3057358c7e6a8550efdb4cc351eb0
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69037881"
---
# <a name="how-to-set-the-image-displayed-by-a-windows-forms-control"></a><span data-ttu-id="8a7b5-102">Instrukcje: Ustawianie obrazu wyświetlanego przez kontrolkę Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8a7b5-102">How to: Set the image displayed by a Windows Forms control</span></span>

<span data-ttu-id="8a7b5-103">Kilka kontrolek Windows Forms może wyświetlać obrazy.</span><span class="sxs-lookup"><span data-stu-id="8a7b5-103">Several Windows Forms controls can display images.</span></span> <span data-ttu-id="8a7b5-104">Te obrazy mogą być ikonami, które wyjaśniają przeznaczenie kontrolki, na przykład ikona dyskietki na przycisku oznaczającego polecenie **Zapisz** .</span><span class="sxs-lookup"><span data-stu-id="8a7b5-104">These images can be icons that clarify the purpose of the control, such as a diskette icon on a button denoting the **Save** command.</span></span> <span data-ttu-id="8a7b5-105">Alternatywnie, ikony mogą być obrazami tła, aby nadać formantowi wygląd i zachowanie.</span><span class="sxs-lookup"><span data-stu-id="8a7b5-105">Alternatively, the icons can be background images to give the control the appearance and behavior you want.</span></span>

## <a name="to-set-the-image-displayed-by-a-control"></a><span data-ttu-id="8a7b5-106">Aby ustawić obraz wyświetlany przez kontrolkę</span><span class="sxs-lookup"><span data-stu-id="8a7b5-106">To set the image displayed by a control</span></span>

1. <span data-ttu-id="8a7b5-107">Ustaw kontrolkę `Image` lub `BackgroundImage` właściwość na obiekt typu <xref:System.Drawing.Image>.</span><span class="sxs-lookup"><span data-stu-id="8a7b5-107">Set the control's `Image` or `BackgroundImage` property to an object of type <xref:System.Drawing.Image>.</span></span> <span data-ttu-id="8a7b5-108">Ogólnie rzecz biorąc, zostanie załadowany obraz z pliku za pomocą <xref:System.Drawing.Image.FromFile%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="8a7b5-108">Generally, you will be loading the image from a file by using the <xref:System.Drawing.Image.FromFile%2A> method.</span></span>

     <span data-ttu-id="8a7b5-109">W poniższym przykładzie kodu ścieżka ustawiona dla lokalizacji obrazu jest folderem **Moje obrazy** .</span><span class="sxs-lookup"><span data-stu-id="8a7b5-109">In the following code example, the path set for the location of the image is the **My Pictures** folder.</span></span> <span data-ttu-id="8a7b5-110">Większość komputerów z systemem operacyjnym Windows będzie zawierać ten katalog.</span><span class="sxs-lookup"><span data-stu-id="8a7b5-110">Most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="8a7b5-111">Dzięki temu użytkownicy mający minimalne poziomy dostępu do systemu mogą bezpiecznie uruchamiać aplikację.</span><span class="sxs-lookup"><span data-stu-id="8a7b5-111">This also enables users with minimal system access levels to run the application safely.</span></span> <span data-ttu-id="8a7b5-112">Poniższy przykład kodu wymaga, aby formularz z <xref:System.Windows.Forms.PictureBox> dodaną kontrolką został już dodany.</span><span class="sxs-lookup"><span data-stu-id="8a7b5-112">The following code example requires that you already have a form with a <xref:System.Windows.Forms.PictureBox> control added.</span></span>

    ```vb
    ' Replace the image named below
    ' with an icon of your own choosing.
    PictureBox1.Image = Image.FromFile _
       (System.Environment.GetFolderPath _
       (System.Environment.SpecialFolder.MyPictures) _
       & "\Image.gif")
    ```

    ```csharp
    // Replace the image named below
    // with an icon of your own choosing.
    // Note the escape character used (@) when specifying the path.
    pictureBox1.Image = Image.FromFile
       (System.Environment.GetFolderPath
       (System.Environment.SpecialFolder.MyPictures)
       + @"\Image.gif");
    ```

    ```cpp
    // Replace the image named below
    // with an icon of your own choosing.
    pictureBox1->Image = Image::FromFile(String::Concat
       (System::Environment::GetFolderPath
       (System::Environment::SpecialFolder::MyPictures),
       "\\Image.gif"));
    ```

## <a name="see-also"></a><span data-ttu-id="8a7b5-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8a7b5-113">See also</span></span>

- <xref:System.Drawing.Image.FromFile%2A>
- <xref:System.Drawing.Image>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
