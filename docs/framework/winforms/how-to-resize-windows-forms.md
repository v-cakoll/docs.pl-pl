---
title: Zmień rozmiar formularza
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- resizing Windows Forms
- Windows Forms, resizing
ms.assetid: 5d9dd47e-e68c-48c9-a0a3-a9ff34ba009d
ms.openlocfilehash: 8d4ce46ada505f952fc3090d10c5d893338d19f2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739307"
---
# <a name="how-to-resize-windows-forms"></a><span data-ttu-id="b6a76-102">Porady: zmienianie rozmiarów formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="b6a76-102">How to: Resize Windows Forms</span></span>

<span data-ttu-id="b6a76-103">Możesz określić rozmiar formularza systemu Windows na kilka sposobów.</span><span class="sxs-lookup"><span data-stu-id="b6a76-103">You can specify the size of your Windows Form in several ways.</span></span> <span data-ttu-id="b6a76-104">Możesz zmienić wysokość i szerokość formularza programowo, ustawiając nową wartość właściwości <xref:System.Windows.Forms.Form.Size%2A> lub odpowiednio dopasowuj właściwości <xref:System.Windows.Forms.Control.Height%2A> lub <xref:System.Windows.Forms.Control.Width%2A>.</span><span class="sxs-lookup"><span data-stu-id="b6a76-104">You can change both the height and the width of the form programmatically by setting a new value for the <xref:System.Windows.Forms.Form.Size%2A> property, or adjust the <xref:System.Windows.Forms.Control.Height%2A> or <xref:System.Windows.Forms.Control.Width%2A> properties individually.</span></span> <span data-ttu-id="b6a76-105">Jeśli używasz programu Visual Studio, możesz zmienić rozmiar przy użyciu Projektant formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="b6a76-105">If you're using Visual Studio, you can change the size using the Windows Forms Designer.</span></span> <span data-ttu-id="b6a76-106">Zobacz również [How to: zmiana rozmiaru Windows Forms przy użyciu narzędzia Projektant](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/37k2zkwx(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="b6a76-106">Also see [How to: Resize Windows Forms Using the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/37k2zkwx(v=vs.100)).</span></span>

## <a name="resize-a-form-programmatically"></a><span data-ttu-id="b6a76-107">Programistyczne Zmienianie rozmiaru formularza</span><span class="sxs-lookup"><span data-stu-id="b6a76-107">Resize a form programmatically</span></span>

<span data-ttu-id="b6a76-108">Zdefiniuj rozmiar formularza w czasie wykonywania przez ustawienie właściwości <xref:System.Windows.Forms.Form.Size%2A> formularza.</span><span class="sxs-lookup"><span data-stu-id="b6a76-108">Define the size of a form at run time by setting the <xref:System.Windows.Forms.Form.Size%2A> property of the form.</span></span>

<span data-ttu-id="b6a76-109">Poniższy przykład kodu pokazuje rozmiar formularza ustawiony na 100 × 100 pikseli.</span><span class="sxs-lookup"><span data-stu-id="b6a76-109">The following code example shows the form size set to 100 × 100 pixels.</span></span>

```vb
Form1.Size = New System.Drawing.Size(100, 100)
```

```csharp
Form1.Size = new System.Drawing.Size(100, 100);
```

```cpp
Form1->Size = System::Drawing::Size(100, 100);
```

## <a name="change-form-width-and-height-programmatically"></a><span data-ttu-id="b6a76-110">Programowo Zmień szerokość i wysokość formularza</span><span class="sxs-lookup"><span data-stu-id="b6a76-110">Change form width and height programmatically</span></span>

<span data-ttu-id="b6a76-111">Po zdefiniowaniu <xref:System.Windows.Forms.Form.Size%2A> Zmień wysokość lub szerokość formularza przy użyciu właściwości <xref:System.Windows.Forms.Control.Width%2A> lub <xref:System.Windows.Forms.Control.Height%2A>.</span><span class="sxs-lookup"><span data-stu-id="b6a76-111">After the <xref:System.Windows.Forms.Form.Size%2A> is defined, change either the form height or width by using the <xref:System.Windows.Forms.Control.Width%2A> or <xref:System.Windows.Forms.Control.Height%2A> properties.</span></span>

<span data-ttu-id="b6a76-112">Poniższy przykład kodu pokazuje szerokość formularza ustawioną na 300 pikseli od lewej krawędzi formularza, natomiast wysokość pozostaje stała.</span><span class="sxs-lookup"><span data-stu-id="b6a76-112">The following code example shows the width of the form set to 300 pixels from the left edge of the form, whereas the height stays constant.</span></span>

```vb
Form1.Width = 300
```

```csharp
Form1.Width = 300;
```

```cpp
Form1->Width = 300;
```

<span data-ttu-id="b6a76-113">—lub—</span><span class="sxs-lookup"><span data-stu-id="b6a76-113">-or-</span></span>

<span data-ttu-id="b6a76-114">Zmień <xref:System.Drawing.Size.Width%2A> lub <xref:System.Drawing.Size.Height%2A>, ustawiając właściwość <xref:System.Windows.Forms.Form.Size%2A>.</span><span class="sxs-lookup"><span data-stu-id="b6a76-114">Change <xref:System.Drawing.Size.Width%2A> or <xref:System.Drawing.Size.Height%2A> by setting the <xref:System.Windows.Forms.Form.Size%2A> property.</span></span>

<span data-ttu-id="b6a76-115">Jednak, jak pokazano w poniższym przykładzie kodu, to podejście jest bardziej uciążliwe niż tylko Ustawianie właściwości <xref:System.Windows.Forms.Control.Width%2A> lub <xref:System.Windows.Forms.Control.Height%2A>.</span><span class="sxs-lookup"><span data-stu-id="b6a76-115">However, as the following code example shows, this approach is more cumbersome than just setting <xref:System.Windows.Forms.Control.Width%2A> or <xref:System.Windows.Forms.Control.Height%2A> properties.</span></span>

```vb
Form1.Size = New Size(300, Form1.Size.Height)
```

```csharp
Form1.Size = new Size(300, Form1.Size.Height);
```

```cpp
Form1->Size = System::Drawing::Size(300, Form1->Size.Height);
```

## <a name="change-form-size-by-increments-programmatically"></a><span data-ttu-id="b6a76-116">Zmienianie rozmiaru formularza przez przyrosty</span><span class="sxs-lookup"><span data-stu-id="b6a76-116">Change form size by increments programmatically</span></span>

<span data-ttu-id="b6a76-117">Aby zwiększyć rozmiar formularza, należy ustawić właściwości <xref:System.Drawing.Size.Width%2A> i <xref:System.Drawing.Size.Height%2A>.</span><span class="sxs-lookup"><span data-stu-id="b6a76-117">To increment the size of the form, set the <xref:System.Drawing.Size.Width%2A> and <xref:System.Drawing.Size.Height%2A> properties.</span></span>

<span data-ttu-id="b6a76-118">Poniższy przykład kodu pokazuje szerokość formularza o 200 pikseli szerszym od bieżącego ustawienia.</span><span class="sxs-lookup"><span data-stu-id="b6a76-118">The following code example shows the width of the form set to 200 pixels wider than the current setting.</span></span>

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
> <span data-ttu-id="b6a76-119">Zawsze używaj właściwości <xref:System.Drawing.Size.Height%2A> lub <xref:System.Drawing.Size.Width%2A>, aby zmienić wymiar formularza, chyba że jednocześnie ustawiono wymiar wysokość i szerokość, ustawiając właściwość <xref:System.Windows.Forms.Form.Size%2A> na nową strukturę <xref:System.Drawing.Size>.</span><span class="sxs-lookup"><span data-stu-id="b6a76-119">Always use the <xref:System.Drawing.Size.Height%2A> or <xref:System.Drawing.Size.Width%2A> property to change a dimension of a form, unless you are setting both height and width dimensions at the same time by setting the <xref:System.Windows.Forms.Form.Size%2A> property to a new <xref:System.Drawing.Size> structure.</span></span> <span data-ttu-id="b6a76-120">Właściwość <xref:System.Windows.Forms.Form.Size%2A> zwraca strukturę <xref:System.Drawing.Size>, która jest typem wartości.</span><span class="sxs-lookup"><span data-stu-id="b6a76-120">The <xref:System.Windows.Forms.Form.Size%2A> property returns a <xref:System.Drawing.Size> structure, which is a value type.</span></span> <span data-ttu-id="b6a76-121">Nie można przypisać nowej wartości do właściwości typu wartości.</span><span class="sxs-lookup"><span data-stu-id="b6a76-121">You cannot assign a new value to the property of a value type.</span></span> <span data-ttu-id="b6a76-122">W związku z tym Poniższy przykład kodu nie zostanie skompilowany.</span><span class="sxs-lookup"><span data-stu-id="b6a76-122">Therefore, the following code example will not compile.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="b6a76-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b6a76-123">See also</span></span>

- [<span data-ttu-id="b6a76-124">Wprowadzenie do formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b6a76-124">Getting Started with Windows Forms</span></span>](getting-started-with-windows-forms.md)
- [<span data-ttu-id="b6a76-125">Rozszerzanie aplikacji Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b6a76-125">Enhancing Windows Forms Applications</span></span>](./advanced/index.md)
