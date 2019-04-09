---
title: GetRawInputDevices
ms.date: 03/30/2017
helpviewer_keywords:
- raw input [WPF]
ms.assetid: c4d37ecd-065a-4d1c-9e6c-26804ae968ca
ms.openlocfilehash: 3531ff9f42289a3ad3b029f090f2dd4987e5886c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59199407"
---
# <a name="getrawinputdevices"></a><span data-ttu-id="3f76a-102">GetRawInputDevices</span><span class="sxs-lookup"><span data-stu-id="3f76a-102">GetRawInputDevices</span></span>
<span data-ttu-id="3f76a-103">Umożliwia PresentationHost.exe odnajdywania nieprzetworzonych danych wejściowych (urządzenia ludzi interfejs), które jest zainteresowany aplikacji hosta.</span><span class="sxs-lookup"><span data-stu-id="3f76a-103">Allows PresentationHost.exe to discover the raw input devices (Human Interface Devices) that the host application is interested in.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f76a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3f76a-104">Syntax</span></span>  
  
```  
HRESULT GetRawInputDevices( [out] IEnumRAWINPUTDEVICE **ppEnum );  
```  
  
## <a name="parameters"></a><span data-ttu-id="3f76a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3f76a-105">Parameters</span></span>  
 `ppEnum`  
  
 <span data-ttu-id="3f76a-106">[out] Wskaźnik do [ienumrawinputdevice —](ienumrawinputdevice.md) wyliczania urządzeniach niesformatowanych danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="3f76a-106">[out] A pointer to an [IEnumRAWINPUTDEVICE](ienumrawinputdevice.md) for enumerating the raw input devices.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="3f76a-107">Wartość właściwości/Zwracana wartość</span><span class="sxs-lookup"><span data-stu-id="3f76a-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="3f76a-108">HRESULT:</span><span class="sxs-lookup"><span data-stu-id="3f76a-108">HRESULT:</span></span>  
  
 <span data-ttu-id="3f76a-109">S_OK - [ienumrawinputdevice —](ienumrawinputdevice.md) tylko będą używane przez PresentationHost.exe, jeśli zostanie zwrócony S_OK.</span><span class="sxs-lookup"><span data-stu-id="3f76a-109">S_OK - [IEnumRAWINPUTDEVICE](ienumrawinputdevice.md) will only be used by PresentationHost.exe if S_OK is returned.</span></span>  
  
 <span data-ttu-id="3f76a-110">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="3f76a-110">E_NOTIMPL</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3f76a-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3f76a-111">Remarks</span></span>  
 <span data-ttu-id="3f76a-112">Urządzeniach niesformatowanych danych wejściowych to zbiór urządzeń, danych wejściowych, obejmującą klawiatur, myszy i mniej tradycyjnych urządzenia, na przykład zdalnego sterowania.</span><span class="sxs-lookup"><span data-stu-id="3f76a-112">Raw input devices are the set of input devices that includes keyboards, mice, and less traditional devices like remote controls.</span></span>  
  
 <span data-ttu-id="3f76a-113">Po pobraniu listy urządzeniach niesformatowanych danych wejściowych PresentationHost.exe rejestruje się za pomocą urządzeń mają otrzymywać powiadomienia WM_INPUT.</span><span class="sxs-lookup"><span data-stu-id="3f76a-113">Once the list of raw input devices has been retrieved, PresentationHost.exe registers with the devices to receive WM_INPUT notification messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f76a-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3f76a-114">See also</span></span>

- [<span data-ttu-id="3f76a-115">GetRawInputDeviceList</span><span class="sxs-lookup"><span data-stu-id="3f76a-115">GetRawInputDeviceList</span></span>](/windows/desktop/api/winuser/nf-winuser-getrawinputdevicelist)
- [<span data-ttu-id="3f76a-116">FilterInputMessage</span><span class="sxs-lookup"><span data-stu-id="3f76a-116">FilterInputMessage</span></span>](filterinputmessage.md)
