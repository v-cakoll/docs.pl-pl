---
title: Udostępnianie dostawcy automatyzacji interfejsu użytkownika po stronie serwera
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- expose a server-side UI Automation provider
- UI Automation, server-side provider, exposing
- server-side UI Automation provider, exposing
ms.assetid: 55d419c0-2201-4101-90c9-2888df4dbb47
ms.openlocfilehash: 8583c82efe341e8ae08ca5ee60bcf1dc8bd40865
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965173"
---
# <a name="expose-a-server-side-ui-automation-provider"></a><span data-ttu-id="f3ab8-102">Udostępnianie dostawcy automatyzacji interfejsu użytkownika po stronie serwera</span><span class="sxs-lookup"><span data-stu-id="f3ab8-102">Expose a Server-side UI Automation Provider</span></span>
> [!NOTE]
> <span data-ttu-id="f3ab8-103">Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych <xref:System.Windows.Automation> w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="f3ab8-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="f3ab8-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie, [Zobacz interfejs API usługi Windows Automation: Automatyzacja](https://go.microsoft.com/fwlink/?LinkID=156746)interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="f3ab8-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="f3ab8-105">Ten temat zawiera przykładowy kod, który pokazuje, jak uwidocznić dostawcę automatyzacji interfejsu użytkownika po stronie serwera, który jest <xref:System.Windows.Forms.Control?displayProperty=nameWithType> hostowany w oknie.</span><span class="sxs-lookup"><span data-stu-id="f3ab8-105">This topic contains example code that shows how to expose a server-side UI Automation provider that is hosted in a <xref:System.Windows.Forms.Control?displayProperty=nameWithType> window.</span></span>  
  
 <span data-ttu-id="f3ab8-106">Przykład przesłania procedurę okna do WM_GETOBJECT pułapki, który jest komunikatem wysyłanym przez [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] usługę podstawową, gdy aplikacja kliencka zażąda informacji o oknie.</span><span class="sxs-lookup"><span data-stu-id="f3ab8-106">The example overrides the window procedure to trap WM_GETOBJECT, which is the message sent by the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] core service when a client application requests information about the window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3ab8-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="f3ab8-107">Example</span></span>  
 [!code-csharp[UIAFragmentProvider_snip#116](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListFragment.cs#116)]
 [!code-vb[UIAFragmentProvider_snip#116](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListFragment.vb#116)]  
  
## <a name="see-also"></a><span data-ttu-id="f3ab8-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f3ab8-108">See also</span></span>

- [<span data-ttu-id="f3ab8-109">Przegląd dostawców automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="f3ab8-109">UI Automation Providers Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)
- [<span data-ttu-id="f3ab8-110">Implementacja dostawcy automatyzacji interfejsu użytkownika po stronie serwera</span><span class="sxs-lookup"><span data-stu-id="f3ab8-110">Server-Side UI Automation Provider Implementation</span></span>](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)
