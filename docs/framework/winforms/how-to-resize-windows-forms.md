---
title: Zmień rozmiar formularza
description: Dowiedz się, jak zmienić wysokość i szerokość formularza, ustawiając nową wartość właściwości size lub odpowiednio dopasowując właściwości Height lub Width.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- resizing Windows Forms
- Windows Forms, resizing
ms.assetid: 5d9dd47e-e68c-48c9-a0a3-a9ff34ba009d
ms.openlocfilehash: 0d6383e4d29d9407d3da97bf8b94761f06d99748
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903275"
---
# <a name="how-to-resize-windows-forms"></a><span data-ttu-id="a7506-103">Instrukcje: Zmienianie rozmiarów formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a7506-103">How to: Resize Windows Forms</span></span>

<span data-ttu-id="a7506-104">Możesz określić rozmiar formularza systemu Windows na kilka sposobów.</span><span class="sxs-lookup"><span data-stu-id="a7506-104">You can specify the size of your Windows Form in several ways.</span></span> <span data-ttu-id="a7506-105">Można zmienić wysokość i szerokość formularza programowo przez ustawienie nowej wartości dla <xref:System.Windows.Forms.Form.Size%2A> właściwości lub dostosowanie <xref:System.Windows.Forms.Control.Height%2A> <xref:System.Windows.Forms.Control.Width%2A> właściwości lub.</span><span class="sxs-lookup"><span data-stu-id="a7506-105">You can change both the height and the width of the form programmatically by setting a new value for the <xref:System.Windows.Forms.Form.Size%2A> property, or adjust the <xref:System.Windows.Forms.Control.Height%2A> or <xref:System.Windows.Forms.Control.Width%2A> properties individually.</span></span> <span data-ttu-id="a7506-106">Jeśli używasz programu Visual Studio, możesz zmienić rozmiar przy użyciu Projektant formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="a7506-106">If you're using Visual Studio, you can change the size using the Windows Forms Designer.</span></span> <span data-ttu-id="a7506-107">Zobacz również [How to: zmiana rozmiaru Windows Forms przy użyciu narzędzia Projektant](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/37k2zkwx(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="a7506-107">Also see [How to: Resize Windows Forms Using the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/37k2zkwx(v=vs.100)).</span></span>

## <a name="resize-a-form-programmatically"></a><span data-ttu-id="a7506-108">Programistyczne Zmienianie rozmiaru formularza</span><span class="sxs-lookup"><span data-stu-id="a7506-108">Resize a form programmatically</span></span>

<span data-ttu-id="a7506-109">Zdefiniuj rozmiar formularza w czasie wykonywania, ustawiając <xref:System.Windows.Forms.Form.Size%2A> Właściwość formularza.</span><span class="sxs-lookup"><span data-stu-id="a7506-109">Define the size of a form at run time by setting the <xref:System.Windows.Forms.Form.Size%2A> property of the form.</span></span>

<span data-ttu-id="a7506-110">Poniższy przykład kodu pokazuje rozmiar formularza ustawiony na 100 × 100 pikseli.</span><span class="sxs-lookup"><span data-stu-id="a7506-110">The following code example shows the form size set to 100 × 100 pixels.</span></span>

```vb
Form1.Size = New System.Drawing.Size(100, 100)
```

```csharp
Form1.Size = new System.Drawing.Size(100, 100);
```

```cpp
Form1->Size = System::Drawing::Size(100, 100);
```

## <a name="change-form-width-and-height-programmatically"></a><span data-ttu-id="a7506-111">Programowo Zmień szerokość i wysokość formularza</span><span class="sxs-lookup"><span data-stu-id="a7506-111">Change form width and height programmatically</span></span>

<span data-ttu-id="a7506-112">Po <xref:System.Windows.Forms.Form.Size%2A> zdefiniowaniu programu Zmień wysokość lub szerokość formularza przy użyciu <xref:System.Windows.Forms.Control.Width%2A> <xref:System.Windows.Forms.Control.Height%2A> właściwości lub.</span><span class="sxs-lookup"><span data-stu-id="a7506-112">After the <xref:System.Windows.Forms.Form.Size%2A> is defined, change either the form height or width by using the <xref:System.Windows.Forms.Control.Width%2A> or <xref:System.Windows.Forms.Control.Height%2A> properties.</span></span>

<span data-ttu-id="a7506-113">Poniższy przykład kodu pokazuje szerokość formularza ustawioną na 300 pikseli od lewej krawędzi formularza, natomiast wysokość pozostaje stała.</span><span class="sxs-lookup"><span data-stu-id="a7506-113">The following code example shows the width of the form set to 300 pixels from the left edge of the form, whereas the height stays constant.</span></span>

```vb
Form1.Width = 300
```

```csharp
Form1.Width = 300;
```

```cpp
Form1->Width = 300;
```

<span data-ttu-id="a7506-114">-lub-</span><span class="sxs-lookup"><span data-stu-id="a7506-114">-or-</span></span>

<span data-ttu-id="a7506-115">Zmień <xref:System.Drawing.Size.Width%2A> lub <xref:System.Drawing.Size.Height%2A> ustawiając <xref:System.Windows.Forms.Form.Size%2A> Właściwość.</span><span class="sxs-lookup"><span data-stu-id="a7506-115">Change <xref:System.Drawing.Size.Width%2A> or <xref:System.Drawing.Size.Height%2A> by setting the <xref:System.Windows.Forms.Form.Size%2A> property.</span></span>

<span data-ttu-id="a7506-116">Jednak, jak pokazano w poniższym przykładzie kodu, to podejście jest bardziej uciążliwe niż tylko ustawienie <xref:System.Windows.Forms.Control.Width%2A> lub <xref:System.Windows.Forms.Control.Height%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="a7506-116">However, as the following code example shows, this approach is more cumbersome than just setting <xref:System.Windows.Forms.Control.Width%2A> or <xref:System.Windows.Forms.Control.Height%2A> properties.</span></span>

```vb
Form1.Size = New Size(300, Form1.Size.Height)
```

```csharp
Form1.Size = new Size(300, Form1.Size.Height);
```

```cpp
Form1->Size = System::Drawing::Size(300, Form1->Size.Height);
```

## <a name="change-form-size-by-increments-programmatically"></a><span data-ttu-id="a7506-117">Zmienianie rozmiaru formularza przez przyrosty</span><span class="sxs-lookup"><span data-stu-id="a7506-117">Change form size by increments programmatically</span></span>

<span data-ttu-id="a7506-118">Aby zwiększyć rozmiar formularza, ustaw <xref:System.Drawing.Size.Width%2A> <xref:System.Drawing.Size.Height%2A> właściwości i.</span><span class="sxs-lookup"><span data-stu-id="a7506-118">To increment the size of the form, set the <xref:System.Drawing.Size.Width%2A> and <xref:System.Drawing.Size.Height%2A> properties.</span></span>

<span data-ttu-id="a7506-119">Poniższy przykład kodu pokazuje szerokość formularza o 200 pikseli szerszym od bieżącego ustawienia.</span><span class="sxs-lookup"><span data-stu-id="a7506-119">The following code example shows the width of the form set to 200 pixels wider than the current setting.</span></span>

```vb
Form1.Width += 200
```

```csharp
Form1.Width += 200;
```

```cpp
Form1->Width += 200;
```

> [!CAUTION]
> <span data-ttu-id="a7506-120">Zawsze używaj <xref:System.Drawing.Size.Height%2A> właściwości lub <xref:System.Drawing.Size.Width%2A> , aby zmienić wymiar formularza, chyba że jednocześnie ustawiono wymiar wysokość i szerokość, ustawiając <xref:System.Windows.Forms.Form.Size%2A> Właściwość na nową <xref:System.Drawing.Size> strukturę.</span><span class="sxs-lookup"><span data-stu-id="a7506-120">Always use the <xref:System.Drawing.Size.Height%2A> or <xref:System.Drawing.Size.Width%2A> property to change a dimension of a form, unless you are setting both height and width dimensions at the same time by setting the <xref:System.Windows.Forms.Form.Size%2A> property to a new <xref:System.Drawing.Size> structure.</span></span> <span data-ttu-id="a7506-121"><xref:System.Windows.Forms.Form.Size%2A>Właściwość zwraca <xref:System.Drawing.Size> strukturę, która jest typem wartości.</span><span class="sxs-lookup"><span data-stu-id="a7506-121">The <xref:System.Windows.Forms.Form.Size%2A> property returns a <xref:System.Drawing.Size> structure, which is a value type.</span></span> <span data-ttu-id="a7506-122">Nie można przypisać nowej wartości do właściwości typu wartości.</span><span class="sxs-lookup"><span data-stu-id="a7506-122">You cannot assign a new value to the property of a value type.</span></span> <span data-ttu-id="a7506-123">W związku z tym Poniższy przykład kodu nie zostanie skompilowany.</span><span class="sxs-lookup"><span data-stu-id="a7506-123">Therefore, the following code example will not compile.</span></span>

```vb
' NOTE: CODE WILL NOT COMPILE
Dim f As New Form()
f.Size.Width += 100
```

```csharp
// NOTE: CODE WILL NOT COMPILE
Form f = new Form();
f.Size.Width += 100;
```

```cpp
// NOTE: CODE WILL NOT COMPILE
Form^ f = gcnew Form();
f->Size->X += 100;
```

## <a name="see-also"></a><span data-ttu-id="a7506-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a7506-124">See also</span></span>

- [<span data-ttu-id="a7506-125">Wprowadzenie do formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="a7506-125">Getting Started with Windows Forms</span></span>](getting-started-with-windows-forms.md)
- [<span data-ttu-id="a7506-126">Rozszerzanie aplikacji Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a7506-126">Enhancing Windows Forms Applications</span></span>](./advanced/index.md)
