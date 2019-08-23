---
title: IWpfHostSupport
ms.date: 03/30/2017
helpviewer_keywords:
- IWpfHostSupport interface [WPF]
ms.assetid: cc5a0281-de81-4cc1-87e4-0e46b1a811e9
ms.openlocfilehash: 994e5146e9cf49a9b31396d0b51e7be83bbb3cfb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964782"
---
# <a name="iwpfhostsupport"></a>IWpfHostSupport
Aplikacje, które [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] obsługują zawartość za pośrednictwem PresentationHost. exe, implementują ten interfejs, aby zapewnić punkt integracji między hostem a PresentationHost. exe.  
  
## <a name="remarks"></a>Uwagi  
 [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]aplikacje, takie jak przeglądarki sieci Web [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] , mogą hostować zawartość, w tym [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] i luźno kod XAML. Aby hostować [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] zawartość [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] , aplikacje tworzą wystąpienie kontrolki [WebBrowser](https://go.microsoft.com/fwlink/?LinkId=97911). Program [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] tworzy wystąpienie programu PresentationHost. exe, które udostępnia hostowaną [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] zawartość hostowi do wyświetlania w [formancie WebBrowser](https://go.microsoft.com/fwlink/?LinkId=97911).  
  
 Integracja włączona, `IWpfHostSupport` umożliwiając programowi PresentationHost. exe:  
  
- Wykrywaj i Rejestruj na nieprzetworzonych urządzeniach wejściowych (urządzenia interfejsu ludzkiego), których aplikacja hosta jest zainteresowana.  
  
- Odbieraj komunikaty wejściowe z zarejestrowanych nieprzetworzonych urządzeń wejściowych i przekazuj odpowiednie komunikaty do aplikacji hosta.  
  
- Zbadaj aplikację hosta pod kątem niestandardowego postępu i błędów interfejsów użytkownika.  
  
> [!NOTE]
> Ten interfejs API jest przeznaczony tylko do użytku i jest obsługiwany na lokalnym komputerze klienckim  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|[GetRawInputDevices](getrawinputdevices.md)|Zezwala programowi PresentationHost. exe na odnajdywanie nieprzetworzonych urządzeń wejściowych (urządzeń z interfejsem ludzkim), których aplikacja hosta interesuje.|  
|[FilterInputMessage](filterinputmessage.md)|Wywoływana przez PresentationHost. exe za każdym razem, gdy wiadomość zostanie odebrana, chyba że zostanie zwrócona wartość E_NOTIMPL.|  
|[GetCustomUI](getcustomui.md)|Domyślnie program PresentationHost. exe udostępnia swój własny postęp wdrażania i interfejsy użytkownika błędów wdrażania, które są wyświetlane podczas wdrażania zawartości WPF.|
