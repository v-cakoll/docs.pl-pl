---
title: 'Instrukcje: Przesłanianie drzewa logicznego'
ms.date: 03/30/2017
helpviewer_keywords:
- overriding the logical tree [WPF]
- logical tree [WPF], overriding
ms.assetid: 0ae4d074-8113-4b06-b4fa-e0f39d4967a6
ms.openlocfilehash: bf3459fff1a90326794d6713dd39c73596b0e960
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61768449"
---
# <a name="how-to-override-the-logical-tree"></a>Instrukcje: Przesłanianie drzewa logicznego
Chociaż nie jest wymagane w większości przypadków, autorzy zaawansowanych kontroli ma możliwość przesłanianie drzewa logicznego.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie przedstawiono sposób podklasy <xref:System.Windows.Controls.StackPanel> w tym przypadku zastąpić drzewo logiczne, aby wymusić zachowanie, że zespół może mieć tylko i będzie renderować obraz tylko jeden typ elementów podrzędnych. To niekoniecznie praktycznie pożądane zachowania, ale jest pokazany tutaj jako środek pokazujący scenariusz zastępowanie elementu normalne drzewo logiczne.  
  
 [!code-csharp[LogicalOverride#SingletonPanel](~/samples/snippets/csharp/VS_Snippets_Wpf/LogicalOverride/CSharp/SDKSampleLibrary/class1.cs#singletonpanel)]  
  
 Aby uzyskać więcej informacji na temat drzewa logicznego, zobacz [drzewa w WPF](trees-in-wpf.md).
