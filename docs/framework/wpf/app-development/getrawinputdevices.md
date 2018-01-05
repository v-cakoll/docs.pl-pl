---
title: GetRawInputDevices
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: raw input [WPF]
ms.assetid: c4d37ecd-065a-4d1c-9e6c-26804ae968ca
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5229eb7e72b63f3e44f67dc750d49acbf44410da
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="getrawinputdevices"></a><span data-ttu-id="fa50c-102">GetRawInputDevices</span><span class="sxs-lookup"><span data-stu-id="fa50c-102">GetRawInputDevices</span></span>
<span data-ttu-id="fa50c-103">Umożliwia PresentationHost.exe w celu odnalezienia urządzeń wejściowych raw (człowieka interfejsu urządzenia), które jest zainteresowana aplikacji hosta.</span><span class="sxs-lookup"><span data-stu-id="fa50c-103">Allows PresentationHost.exe to discover the raw input devices (Human Interface Devices) that the host application is interested in.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa50c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fa50c-104">Syntax</span></span>  
  
```  
HRESULT GetRawInputDevices( [out] IEnumRAWINPUTDEVICE **ppEnum );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fa50c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fa50c-105">Parameters</span></span>  
 `ppEnum`  
  
 <span data-ttu-id="fa50c-106">[out] Wskaźnik do [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) wyliczania raw urządzenia wejściowego.</span><span class="sxs-lookup"><span data-stu-id="fa50c-106">[out] A pointer to an [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) for enumerating the raw input devices.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="fa50c-107">Wartość właściwości/Zwracana wartość</span><span class="sxs-lookup"><span data-stu-id="fa50c-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="fa50c-108">WYNIK HRESULT:</span><span class="sxs-lookup"><span data-stu-id="fa50c-108">HRESULT:</span></span>  
  
 <span data-ttu-id="fa50c-109">S_OK - [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) tylko będą używane przez PresentationHost.exe, jeśli jest zwracana wartość S_OK.</span><span class="sxs-lookup"><span data-stu-id="fa50c-109">S_OK - [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) will only be used by PresentationHost.exe if S_OK is returned.</span></span>  
  
 <span data-ttu-id="fa50c-110">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="fa50c-110">E_NOTIMPL</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fa50c-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fa50c-111">Remarks</span></span>  
 <span data-ttu-id="fa50c-112">Nieprzetworzone urządzenia wejściowe są zbiór urządzeń wejściowych obejmuje klawiatury, myszy i mniej tradycyjnych urządzeniami, takimi jak zdalnego sterowania.</span><span class="sxs-lookup"><span data-stu-id="fa50c-112">Raw input devices are the set of input devices that includes keyboards, mice, and less traditional devices like remote controls.</span></span>  
  
 <span data-ttu-id="fa50c-113">Po pobraniu listy urządzeń wejściowych raw PresentationHost.exe rejestruje urządzenia odbierają powiadomienia WM_INPUT.</span><span class="sxs-lookup"><span data-stu-id="fa50c-113">Once the list of raw input devices has been retrieved, PresentationHost.exe registers with the devices to receive WM_INPUT notification messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa50c-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fa50c-114">See Also</span></span>  
 [<span data-ttu-id="fa50c-115">http://msdn.microsoft.com/library/default.asp?URL=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputfunctions/getrawinputdevicelist.asp</span><span class="sxs-lookup"><span data-stu-id="fa50c-115">http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputfunctions/getrawinputdevicelist.asp</span></span>](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputfunctions/getrawinputdevicelist.asp)  
 [<span data-ttu-id="fa50c-116">FilterInputMessage</span><span class="sxs-lookup"><span data-stu-id="fa50c-116">FilterInputMessage</span></span>](../../../../docs/framework/wpf/app-development/filterinputmessage.md)
