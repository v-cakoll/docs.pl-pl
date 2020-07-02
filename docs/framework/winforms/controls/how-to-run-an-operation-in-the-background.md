---
title: 'Porady: uruchamianie operacji w tle'
description: Dowiedz się, jak używać klasy BackgroundWorker do uruchamiania czasochłonnej operacji Windows Forms w tle.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- background tasks
- forms [Windows Forms], multithreading
- forms [Windows Forms], background operations
- background threads
- BackgroundWorker class [Windows Forms], examples
- threading [Windows Forms], background operations
- background operations
ms.assetid: 5b56e2aa-dc05-444f-930c-2d7b23f9ad5b
ms.openlocfilehash: 6b2a97f5acf1e906dfe141aee62e99a4e50dca9f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621577"
---
# <a name="how-to-run-an-operation-in-the-background"></a>Porady: uruchamianie operacji w tle
Jeśli masz dużo czasu na ukończenie operacji, która nie ma być przyczyną opóźnień w interfejsie użytkownika, możesz użyć <xref:System.ComponentModel.BackgroundWorker> klasy do uruchomienia operacji w innym wątku.  
  
 Poniższy przykład kodu pokazuje, jak uruchomić czasochłonną operację w tle. Formularz zawiera przyciski **Start** i **Cancel** . Kliknij przycisk **Uruchom** , aby uruchomić operację asynchroniczną. Kliknij przycisk **Anuluj** , aby zatrzymać uruchomioną operację asynchroniczną. Wyniki każdej operacji są wyświetlane w <xref:System.Windows.Forms.MessageBox> .  
  
 W programie Visual Studio jest dostępna szeroka pomoc techniczna dla tego zadania.  
  
 Zobacz również [Przewodnik: uruchamianie operacji w tle](walkthrough-running-an-operation-in-the-background.md).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.ComponentModel.BackgroundWorker.Example#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker.Example#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Odwołania do zestawów system, system. Drawing i system. Windows. Forms.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ComponentModel.BackgroundWorker>
- <xref:System.ComponentModel.DoWorkEventArgs>
- [Instrukcje: implementowanie formularza korzystającego z operacji w tle](how-to-implement-a-form-that-uses-a-background-operation.md)
- [BackgroundWorker, składnik](backgroundworker-component.md)
