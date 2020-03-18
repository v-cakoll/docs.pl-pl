---
title: Przykładowa klasa COM — przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- examples [C#], COM classes
- COM, exposing Visual C# objects to
ms.assetid: 6504dea9-ad1c-4993-a794-830fec5270af
ms.openlocfilehash: 6af85d0314a44acbde0996cecbe6dad82cdcc8db
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712081"
---
# <a name="example-com-class-c-programming-guide"></a>Klasa COM — Przykład (Przewodnik programowania w języku C#)
Poniżej przedstawiono przykład klasy, które można udostępnić jako com obiektu. Po umieszczeniu tego kodu w pliku .cs i dodaniu do projektu ustaw właściwość **Zarejestruj dla COM Interop** na **True**. Aby uzyskać więcej informacji, zobacz [Jak: Zarejestrować składnik dla COM Interop](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w29wacsy(v=vs.100)).
  
 Wystawianie obiektów Visual C# do com wymaga deklarowania interfejsu klasy, interfejs zdarzeń, jeśli jest to wymagane, a sama klasa. Członkowie klasy muszą przestrzegać tych zasad, aby były widoczne dla COM:  
  
- Klasa musi być publiczna.  
  
- Właściwości, metody i zdarzenia muszą być publiczne.  
  
- Właściwości i metody muszą być zadeklarowane w interfejsie klasy.  
  
- Zdarzenia muszą być zadeklarowane w interfejsie zdarzenia.  
  
 Inne elementy publiczne w klasie, które nie są zadeklarowane w tych interfejsach nie będą widoczne dla com, ale będą widoczne dla innych obiektów .NET Framework.  
  
 Aby udostępnić właściwości i metody do com, należy zadeklarować je `DispId` w interfejsie klasy i oznaczyć je z atrybutem i zaimplementować je w klasie. Kolejność, w jakiej elementy członkowskie są deklarowane w interfejsie jest kolejność używana dla tabeli vtable COM.  
  
 Aby udostępnić zdarzenia z klasy, należy zadeklarować je w `DispId` interfejsie zdarzeń i oznaczyć je atrybutem. Klasa nie powinna implementować tego interfejsu.  
  
 Klasa implementuje interfejs klasy; można zaimplementować więcej niż jeden interfejs, ale pierwsza implementacja będzie domyślny interfejs klasy. Zaimplementuj metody i właściwości udostępniane com tutaj. Muszą być oznaczone jako publiczne i muszą być zgodne z deklaracjami w interfejsie klasy. Ponadto zadeklarować zdarzenia wywoływane przez klasę tutaj. Muszą być oznaczone jako publiczne i muszą być zgodne z deklaracjami w interfejsie zdarzenia.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideInterop#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/ExampleCOM.cs#8)]  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Współdziałanie](./index.md)
- [Strona kompilacji, Projektant projektu (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp)
