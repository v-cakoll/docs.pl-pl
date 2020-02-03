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
# <a name="how-to-resize-windows-forms"></a>Porady: zmienianie rozmiarów formularzy systemu Windows

Możesz określić rozmiar formularza systemu Windows na kilka sposobów. Możesz zmienić wysokość i szerokość formularza programowo, ustawiając nową wartość właściwości <xref:System.Windows.Forms.Form.Size%2A> lub odpowiednio dopasowuj właściwości <xref:System.Windows.Forms.Control.Height%2A> lub <xref:System.Windows.Forms.Control.Width%2A>. Jeśli używasz programu Visual Studio, możesz zmienić rozmiar przy użyciu Projektant formularzy systemu Windows. Zobacz również [How to: zmiana rozmiaru Windows Forms przy użyciu narzędzia Projektant](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/37k2zkwx(v=vs.100)).

## <a name="resize-a-form-programmatically"></a>Programistyczne Zmienianie rozmiaru formularza

Zdefiniuj rozmiar formularza w czasie wykonywania przez ustawienie właściwości <xref:System.Windows.Forms.Form.Size%2A> formularza.

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

Po zdefiniowaniu <xref:System.Windows.Forms.Form.Size%2A> Zmień wysokość lub szerokość formularza przy użyciu właściwości <xref:System.Windows.Forms.Control.Width%2A> lub <xref:System.Windows.Forms.Control.Height%2A>.

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

—lub—

Zmień <xref:System.Drawing.Size.Width%2A> lub <xref:System.Drawing.Size.Height%2A>, ustawiając właściwość <xref:System.Windows.Forms.Form.Size%2A>.

Jednak, jak pokazano w poniższym przykładzie kodu, to podejście jest bardziej uciążliwe niż tylko Ustawianie właściwości <xref:System.Windows.Forms.Control.Width%2A> lub <xref:System.Windows.Forms.Control.Height%2A>.

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

Aby zwiększyć rozmiar formularza, należy ustawić właściwości <xref:System.Drawing.Size.Width%2A> i <xref:System.Drawing.Size.Height%2A>.

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
> Zawsze używaj właściwości <xref:System.Drawing.Size.Height%2A> lub <xref:System.Drawing.Size.Width%2A>, aby zmienić wymiar formularza, chyba że jednocześnie ustawiono wymiar wysokość i szerokość, ustawiając właściwość <xref:System.Windows.Forms.Form.Size%2A> na nową strukturę <xref:System.Drawing.Size>. Właściwość <xref:System.Windows.Forms.Form.Size%2A> zwraca strukturę <xref:System.Drawing.Size>, która jest typem wartości. Nie można przypisać nowej wartości do właściwości typu wartości. W związku z tym Poniższy przykład kodu nie zostanie skompilowany.

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

## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do formularzy Windows Forms](getting-started-with-windows-forms.md)
- [Rozszerzanie aplikacji Windows Forms](./advanced/index.md)
