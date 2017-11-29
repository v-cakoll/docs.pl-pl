---
title: "Udostępnianie dostawcy automatyzacji interfejsu użytkownika po stronie serwera"
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
- expose a server-side UI Automation provider
- UI Automation, server-side provider, exposing
- server-side UI Automation provider, exposing
ms.assetid: 55d419c0-2201-4101-90c9-2888df4dbb47
caps.latest.revision: "20"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: ef4feb52dee26789e7915d108fbd457affcfcff2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="expose-a-server-side-ui-automation-provider"></a><span data-ttu-id="8404b-102">Udostępnianie dostawcy automatyzacji interfejsu użytkownika po stronie serwera</span><span class="sxs-lookup"><span data-stu-id="8404b-102">Expose a Server-side UI Automation Provider</span></span>
> [!NOTE]
>  <span data-ttu-id="8404b-103">Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="8404b-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="8404b-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="8404b-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="8404b-105">Ten temat zawiera przykładowy kod, pokazujący sposób udostępnianie dostawcy automatyzacji interfejsu użytkownika po stronie serwera, który znajduje się w <xref:System.Windows.Forms.Control?displayProperty=nameWithType> okna.</span><span class="sxs-lookup"><span data-stu-id="8404b-105">This topic contains example code that shows how to expose a server-side UI Automation provider that is hosted in a <xref:System.Windows.Forms.Control?displayProperty=nameWithType> window.</span></span>  
  
 <span data-ttu-id="8404b-106">Przykład zastąpienia procedurę okna WM_GETOBJECT, który jest komunikat pułapki wysyłane przez [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] podstawowe usługi, gdy aplikacja kliencka żąda informacji na temat okna.</span><span class="sxs-lookup"><span data-stu-id="8404b-106">The example overrides the window procedure to trap WM_GETOBJECT, which is the message sent by the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] core service when a client application requests information about the window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8404b-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="8404b-107">Example</span></span>  
 [!code-csharp[UIAFragmentProvider_snip#116](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListFragment.cs#116)]
 [!code-vb[UIAFragmentProvider_snip#116](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListFragment.vb#116)]  
  
## <a name="see-also"></a><span data-ttu-id="8404b-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8404b-108">See Also</span></span>  
 [<span data-ttu-id="8404b-109">Przegląd dostawców automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="8404b-109">UI Automation Providers Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)  
 [<span data-ttu-id="8404b-110">Implementacja dostawcy automatyzacji interfejsu użytkownika po stronie serwera</span><span class="sxs-lookup"><span data-stu-id="8404b-110">Server-Side UI Automation Provider Implementation</span></span>](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)
