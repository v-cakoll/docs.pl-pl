---
title: 'Instrukcje: Zmienianie rozmiarów formularzy Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- resizing Windows Forms
- Windows Forms, resizing
ms.assetid: 5d9dd47e-e68c-48c9-a0a3-a9ff34ba009d
ms.openlocfilehash: aa7ee2bbbf6983a371ea71edc0dfd0cc12cd0c9d
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211667"
---
# <a name="how-to-resize-windows-forms"></a>Instrukcje: Zmienianie rozmiarów formularzy Windows Forms

Rozmiar formularza Windows można określić na kilka sposobów. Można zmienić wysokość i szerokość formularza programowo, ustawiając nową wartość dla <xref:System.Windows.Forms.Form.Size%2A> właściwości lub dostosować <xref:System.Windows.Forms.Control.Height%2A> lub <xref:System.Windows.Forms.Control.Width%2A> właściwości indywidualnie. Jeśli używasz programu Visual Studio, możesz zmienić rozmiar przy użyciu programu Windows Forms Designer. Zobacz też [jak: Zmiana rozmiaru formularzy Windows za pomocą projektanta](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/37k2zkwx(v=vs.100)).

## <a name="resize-a-form-programmatically"></a>Programowo zmienić rozmiar formularza

Określ rozmiar formularza w czasie wykonywania, ustawiając <xref:System.Windows.Forms.Form.Size%2A> właściwości formularza.

Poniższy przykład kodu pokazuje rozmiar formularza, równa 100 x 100 pikseli.

```vb
Form1.Size = New System.Drawing.Size(100, 100)
```

```csharp
Form1.Size = new System.Drawing.Size(100, 100);
```

```cpp
Form1->Size = System::Drawing::Size(100, 100);
```

## <a name="change-form-width-and-height-programmatically"></a>Programowe zmienianie wysokość i szerokość formularza

Po <xref:System.Windows.Forms.Form.Size%2A> jest zdefiniowany, zmienić za pomocą formularza wysokość lub szerokość <xref:System.Windows.Forms.Control.Width%2A> lub <xref:System.Windows.Forms.Control.Height%2A> właściwości.

Poniższy przykład kodu pokazuje szerokość formularza, wartość 300 pikseli od lewej krawędzi formularza, natomiast wysokość pozostają stałe.

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

Zmiana <xref:System.Drawing.Size.Width%2A> lub <xref:System.Drawing.Size.Height%2A> , ustawiając <xref:System.Windows.Forms.Form.Size%2A> właściwości.

Jednakże, jak pokazano w poniższym przykładzie kodu, to podejście jest bardziej skomplikowane niż ustawienie tylko <xref:System.Windows.Forms.Control.Width%2A> lub <xref:System.Windows.Forms.Control.Height%2A> właściwości.

```vb
Form1.Size = New Size(300, Form1.Size.Height)
```

```csharp
Form1.Size = new Size(300, Form1.Size.Height);
```

```cpp
Form1->Size = System::Drawing::Size(300, Form1->Size.Height);
```

## <a name="change-form-size-by-increments-programmatically"></a>Zmień rozmiar formularza krokami programowania

Aby zwiększyć rozmiar formularza, ustaw <xref:System.Drawing.Size.Width%2A> i <xref:System.Drawing.Size.Height%2A> właściwości.

Poniższy przykład kodu pokazuje szerokość formularza ustawiona na 200 pikseli szerszy niż bieżące ustawienie.

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
> Zawsze używaj <xref:System.Drawing.Size.Height%2A> lub <xref:System.Drawing.Size.Width%2A> właściwości do zmiany wymiar formularza, chyba że ustawiasz szerokość i wysokość wymiarów w tym samym czasie, ustawiając <xref:System.Windows.Forms.Form.Size%2A> nową właściwość <xref:System.Drawing.Size> struktury. <xref:System.Windows.Forms.Form.Size%2A> Właściwość zwraca <xref:System.Drawing.Size> struktury, która jest typem wartości. Nowa wartość nie można przypisać do właściwości typu wartości. W związku z tym nie zostanie skompilowany w poniższym przykładzie kodu.

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
