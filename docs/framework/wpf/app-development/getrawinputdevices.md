---
title: GetRawInputDevices
ms.date: 03/30/2017
helpviewer_keywords:
- raw input [WPF]
ms.assetid: c4d37ecd-065a-4d1c-9e6c-26804ae968ca
ms.openlocfilehash: 1611183dc02e46ea6d5fbb53c26500be3ed93d0d
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2018
ms.locfileid: "43483953"
---
# <a name="getrawinputdevices"></a><span data-ttu-id="d588b-102">GetRawInputDevices</span><span class="sxs-lookup"><span data-stu-id="d588b-102">GetRawInputDevices</span></span>
<span data-ttu-id="d588b-103">Umożliwia PresentationHost.exe odnajdywania nieprzetworzonych danych wejściowych (urządzenia ludzi interfejs), które jest zainteresowany aplikacji hosta.</span><span class="sxs-lookup"><span data-stu-id="d588b-103">Allows PresentationHost.exe to discover the raw input devices (Human Interface Devices) that the host application is interested in.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d588b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d588b-104">Syntax</span></span>  
  
```  
HRESULT GetRawInputDevices( [out] IEnumRAWINPUTDEVICE **ppEnum );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d588b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d588b-105">Parameters</span></span>  
 `ppEnum`  
  
 <span data-ttu-id="d588b-106">[out] Wskaźnik do [ienumrawinputdevice —](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) wyliczania urządzeniach niesformatowanych danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="d588b-106">[out] A pointer to an [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) for enumerating the raw input devices.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="d588b-107">Wartość właściwości/Zwracana wartość</span><span class="sxs-lookup"><span data-stu-id="d588b-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="d588b-108">HRESULT:</span><span class="sxs-lookup"><span data-stu-id="d588b-108">HRESULT:</span></span>  
  
 <span data-ttu-id="d588b-109">S_OK - [ienumrawinputdevice —](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) tylko będą używane przez PresentationHost.exe, jeśli zostanie zwrócony S_OK.</span><span class="sxs-lookup"><span data-stu-id="d588b-109">S_OK - [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) will only be used by PresentationHost.exe if S_OK is returned.</span></span>  
  
 <span data-ttu-id="d588b-110">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="d588b-110">E_NOTIMPL</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d588b-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d588b-111">Remarks</span></span>  
 <span data-ttu-id="d588b-112">Urządzeniach niesformatowanych danych wejściowych to zbiór urządzeń, danych wejściowych, obejmującą klawiatur, myszy i mniej tradycyjnych urządzenia, na przykład zdalnego sterowania.</span><span class="sxs-lookup"><span data-stu-id="d588b-112">Raw input devices are the set of input devices that includes keyboards, mice, and less traditional devices like remote controls.</span></span>  
  
 <span data-ttu-id="d588b-113">Po pobraniu listy urządzeniach niesformatowanych danych wejściowych PresentationHost.exe rejestruje się za pomocą urządzeń mają otrzymywać powiadomienia WM_INPUT.</span><span class="sxs-lookup"><span data-stu-id="d588b-113">Once the list of raw input devices has been retrieved, PresentationHost.exe registers with the devices to receive WM_INPUT notification messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d588b-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d588b-114">See Also</span></span>  
 [http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputfunctions/getrawinputdevicelist.asp](https://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputfunctions/getrawinputdevicelist.asp)  
 [<span data-ttu-id="d588b-115">FilterInputMessage</span><span class="sxs-lookup"><span data-stu-id="d588b-115">FilterInputMessage</span></span>](../../../../docs/framework/wpf/app-development/filterinputmessage.md)
