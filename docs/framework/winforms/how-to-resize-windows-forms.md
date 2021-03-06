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
# <a name="how-to-resize-windows-forms"></a>Instrukcje: Zmienianie rozmiarów formularzy Windows Forms

Możesz określić rozmiar formularza systemu Windows na kilka sposobów. Można zmienić wysokość i szerokość formularza programowo przez ustawienie nowej wartości dla <xref:System.Windows.Forms.Form.Size%2A> właściwości lub dostosowanie <xref:System.Windows.Forms.Control.Height%2A> <xref:System.Windows.Forms.Control.Width%2A> właściwości lub. Jeśli używasz programu Visual Studio, możesz zmienić rozmiar przy użyciu Projektant formularzy systemu Windows. Zobacz również [How to: zmiana rozmiaru Windows Forms przy użyciu narzędzia Projektant](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/37k2zkwx(v=vs.100)).

## <a name="resize-a-form-programmatically"></a>Programistyczne Zmienianie rozmiaru formularza

Zdefiniuj rozmiar formularza w czasie wykonywania, ustawiając <xref:System.Windows.Forms.Form.Size%2A> Właściwość formularza.

Poniższy przykład kodu pokazuje rozmiar formularza ustawiony na 100 × 100 pikseli.

```vb
Form1.Size = New System.Drawing.Size(100, 100)
```

```csharp
Form1.Size = new System.Drawing.Size(100, 100);
```

```cpp
Form1->Size = System::Drawing::Size(100, 100);
```

## <a name="change-form-width-and-height-programmatically"></a>Programowo Zmień szerokość i wysokość formularza

Po <xref:System.Windows.Forms.Form.Size%2A> zdefiniowaniu programu Zmień wysokość lub szerokość formularza przy użyciu <xref:System.Windows.Forms.Control.Width%2A> <xref:System.Windows.Forms.Control.Height%2A> właściwości lub.

Poniższy przykład kodu pokazuje szerokość formularza ustawioną na 300 pikseli od lewej krawędzi formularza, natomiast wysokość pozostaje stała.

```vb
Form1.Width = 300
```

```csharp
Form1.Width = 300;
```

```cpp
Form1->Width = 300;
```

-lub-

Zmień <xref:System.Drawing.Size.Width%2A> lub <xref:System.Drawing.Size.Height%2A> ustawiając <xref:System.Windows.Forms.Form.Size%2A> Właściwość.

Jednak, jak pokazano w poniższym przykładzie kodu, to podejście jest bardziej uciążliwe niż tylko ustawienie <xref:System.Windows.Forms.Control.Width%2A> lub <xref:System.Windows.Forms.Control.Height%2A> właściwości.

```vb
Form1.Size = New Size(300, Form1.Size.Height)
```

```csharp
Form1.Size = new Size(300, Form1.Size.Height);
```

```cpp
Form1->Size = System::Drawing::Size(300, Form1->Size.Height);
```

## <a name="change-form-size-by-increments-programmatically"></a>Zmienianie rozmiaru formularza przez przyrosty

Aby zwiększyć rozmiar formularza, ustaw <xref:System.Drawing.Size.Width%2A> <xref:System.Drawing.Size.Height%2A> właściwości i.

Poniższy przykład kodu pokazuje szerokość formularza o 200 pikseli szerszym od bieżącego ustawienia.

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
> Zawsze używaj <xref:System.Drawing.Size.Height%2A> właściwości lub <xref:System.Drawing.Size.Width%2A> , aby zmienić wymiar formularza, chyba że jednocześnie ustawiono wymiar wysokość i szerokość, ustawiając <xref:System.Windows.Forms.Form.Size%2A> Właściwość na nową <xref:System.Drawing.Size> strukturę. <xref:System.Windows.Forms.Form.Size%2A>Właściwość zwraca <xref:System.Drawing.Size> strukturę, która jest typem wartości. Nie można przypisać nowej wartości do właściwości typu wartości. W związku z tym Poniższy przykład kodu nie zostanie skompilowany.

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

## <a name="see-also"></a>Zobacz też

- [Wprowadzenie do formularzy systemu Windows](getting-started-with-windows-forms.md)
- [Rozszerzanie aplikacji Windows Forms](./advanced/index.md)
