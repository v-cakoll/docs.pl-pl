---
title: "Rejestrowanie zestawów dostawcy po stronie klienta"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- registering client-side provider assemblies
- client-side provider assemblies, registering
- UI Automation, registering provider assemblies
- provider assemblies, registering
ms.assetid: a03af4d9-2771-43cc-b07b-d468dca23190
caps.latest.revision: "8"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 638e7b07c159bf1daf91428a1b95a4e83f61dace
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="register-a-client-side-provider-assembly"></a>Rejestrowanie zestawów dostawcy po stronie klienta
> [!NOTE]
>  Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 W tym temacie pokazano, jak zarejestrować bibliotekę DLL, która zawiera dostawców automatyzacji interfejsu użytkownika po stronie klienta.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób rejestrowania zestaw zawierający dostawcę dla okna konsoli.  
  
 [!code-csharp[UIAClientSideProvider_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/CSClientProgram.cs#102)]
 [!code-vb[UIAClientSideProvider_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/csclientprogram.vb#102)]  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie dostawcy automatyzacji interfejsu użytkownika po stronie klienta](../../../docs/framework/ui-automation/create-a-client-side-ui-automation-provider.md)
