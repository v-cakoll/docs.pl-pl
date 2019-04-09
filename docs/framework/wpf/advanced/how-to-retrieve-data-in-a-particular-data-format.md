---
title: 'Instrukcje: Uzyskiwanie danych w konkretnym formacie danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drag-and-drop [WPF], retrieving data
- DataFormats class [WPF], retrieving data
- DataObject class [WPF], retrieving data
ms.assetid: a625acf3-1144-44cd-add7-456aefc3859f
ms.openlocfilehash: b3ec1b8fa873fd449956912e9e77e98b0362cb0e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59080023"
---
# <a name="how-to-retrieve-data-in-a-particular-data-format"></a>Instrukcje: Uzyskiwanie danych w konkretnym formacie danych
Poniższe przykłady pokazują, jak można pobrać danych z obiektu danych w określonym formacie.  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Poniższy przykład kodu używa <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> przeładowania najpierw sprawdzić, jeśli określone dane formatu jest dostępna (natywnej lub automatyczna konwersja); Jeśli określony format jest dostępny, przykład pobiera dane przy użyciu <xref:System.Windows.DataObject.GetData%28System.String%29> metody.  
  
### <a name="code"></a>Kod  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat)]  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Poniższy przykład kodu używa <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> przeładowania najpierw sprawdź, czy format danych określony jest natywnie dostępny (formaty danych automatycznie przekonwertować są filtrowane); Jeśli określony format jest dostępny, przykład pobiera dane przy użyciu <xref:System.Windows.DataObject.GetData%28System.String%29>metody.  
  
### <a name="code"></a>Kod  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat_Native](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat_native)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat_Native](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat_native)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.IDataObject>
- [Przegląd Przeciąganie i upuszczanie](drag-and-drop-overview.md)
