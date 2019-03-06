---
title: 'Instrukcje: Zastąp drzewo logiczne'
ms.date: 03/30/2017
helpviewer_keywords:
- overriding the logical tree [WPF]
- logical tree [WPF], overriding
ms.assetid: 0ae4d074-8113-4b06-b4fa-e0f39d4967a6
ms.openlocfilehash: bf3459fff1a90326794d6713dd39c73596b0e960
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57375229"
---
# <a name="how-to-override-the-logical-tree"></a>Instrukcje: Zastąp drzewo logiczne
Chociaż nie jest wymagane w większości przypadków, autorzy zaawansowanych kontroli ma możliwość przesłanianie drzewa logicznego.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie przedstawiono sposób podklasy <xref:System.Windows.Controls.StackPanel> w tym przypadku zastąpić drzewo logiczne, aby wymusić zachowanie, że zespół może mieć tylko i będzie renderować obraz tylko jeden typ elementów podrzędnych. To niekoniecznie praktycznie pożądane zachowania, ale jest pokazany tutaj jako środek pokazujący scenariusz zastępowanie elementu normalne drzewo logiczne.  
  
 [!code-csharp[LogicalOverride#SingletonPanel](~/samples/snippets/csharp/VS_Snippets_Wpf/LogicalOverride/CSharp/SDKSampleLibrary/class1.cs#singletonpanel)]  
  
 Aby uzyskać więcej informacji na temat drzewa logicznego, zobacz [drzewa w WPF](trees-in-wpf.md).
