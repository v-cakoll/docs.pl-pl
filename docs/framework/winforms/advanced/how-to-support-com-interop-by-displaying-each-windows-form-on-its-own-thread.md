---
title: 'Instrukcje: Obsługa międzyoperacyjności modelu COM za pomocą wyświetlania każdego formularza systemu Windows w jego własnym wątku'
ms.date: 03/30/2017
dev_langs:
- vb
helpviewer_keywords:
- COM interop [Windows Forms], Windows Forms
- COM [Windows Forms]
- Windows Forms, unmanaged
- ActiveX controls [Windows Forms], COM interop
- Windows Forms, interop
ms.assetid: a9e04765-d2de-4389-a494-a9a6d07aa6ee
ms.openlocfilehash: 41af4d81995a0a4eac912ecce7dc70cf04f012cd
ms.sourcegitcommit: 1e72e2990220b3635cebc39586828af9deb72d8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2019
ms.locfileid: "71306378"
---
# <a name="how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread"></a>Instrukcje: Obsługa międzyoperacyjności modelu COM przez wyświetlanie każdego formularza systemu Windows w jego własnym wątku

Problemy ze współdziałaniem modelu COM można rozwiązać, wyświetlając formularz w pętli .NET Framework komunikatów, którą można utworzyć za pomocą <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> metody.

Aby formularz systemu Windows działał prawidłowo z aplikacji klienckiej modelu COM, należy uruchomić formularz w pętli komunikatów Windows Forms. W tym celu należy użyć jednej z następujących metod:

- <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> Użyj metody, aby wyświetlić formularz systemu Windows. Aby uzyskać więcej informacji, zobacz [jak: Obsługa międzyoperacyjności modelu COM przez wyświetlanie formularza systemu Windows przy](com-interop-by-displaying-a-windows-form-shadow.md)użyciu metody ShowDialog.

- Wyświetl Każdy formularz systemu Windows w osobnym wątku.

W programie Visual Studio jest dostępna szeroka obsługa tej funkcji.

Zobacz [również przewodnik: Obsługa międzyoperacyjności modelu COM przez wyświetlanie każdego formularza systemu Windows](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233639(v=vs.100))w jego własnym wątku.

## <a name="example"></a>Przykład

Poniższy przykład kodu pokazuje, jak wyświetlić formularz w osobnym wątku i wywołać <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> metodę, aby uruchomić Windows Forms pompę komunikatów na tym wątku. Aby użyć tej metody, należy zorganizować wszystkie wywołania formularza z niezarządzanej aplikacji za pomocą <xref:System.Windows.Forms.Control.Invoke%2A> metody.

Takie podejście wymaga, aby każde wystąpienie formularza było uruchamiane we własnym wątku przy użyciu własnej pętli komunikatów. Na wątek nie może być uruchomiona więcej niż jedna pętla komunikatów. W związku z tym nie można zmienić pętli komunikatów aplikacji klienta. Można jednak zmodyfikować składnik .NET Framework, aby uruchomić nowy wątek, który używa własnej pętli komunikatów.

[!code-vb[System.Windows.Forms.ComInterop#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/COMForm.vb#1)]

[!code-vb[System.Windows.Forms.ComInterop#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/FormManager.vb#10)]

[!code-vb[System.Windows.Forms.ComInterop#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/Form1.vb#100)]

## <a name="compile-the-code"></a>Skompilować kod

`COMForm`Skompiluj, `Form1`, `COMWinform.dll`i `FormManager` , do zestawu o nazwie. Zarejestrowanie zestawu dla współdziałania z modelem COM przy użyciu jednej z metod opisanych w pakiecie [pakowanie zestawu dla modelu COM](../../interop/packaging-an-assembly-for-com.md). Teraz można używać zestawu i odpowiedniego pliku biblioteki typów (TLB) w aplikacjach niezarządzanych. Można na przykład użyć biblioteki typów jako odniesienia w projekcie wykonywalnym Visual Basic 6,0.

## <a name="see-also"></a>Zobacz także

- [Udostępnianie składników .NET Framework modelowi COM](../../interop/exposing-dotnet-components-to-com.md)
- [Pakowanie zestawu dla modelu COM](../../interop/packaging-an-assembly-for-com.md)
- [Rejestrowanie zestawów do użycia z modelem COM](../../interop/registering-assemblies-with-com.md)
- [Instrukcje: Obsługa międzyoperacyjności modelu COM przez wyświetlanie formularza systemu Windows przy użyciu metody ShowDialog](com-interop-by-displaying-a-windows-form-shadow.md)
- [Przegląd formularzy Windows Forms i niezarządzanych aplikacji](windows-forms-and-unmanaged-applications-overview.md)
