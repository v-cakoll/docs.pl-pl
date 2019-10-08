---
title: IWpfHostSupport
ms.date: 03/30/2017
helpviewer_keywords:
- IWpfHostSupport interface [WPF]
ms.assetid: cc5a0281-de81-4cc1-87e4-0e46b1a811e9
ms.openlocfilehash: 85309e46403b2f22f9afb760d4c4ae370c39246b
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004090"
---
# <a name="iwpfhostsupport"></a>IWpfHostSupport
Aplikacje obsługujące zawartość [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] za pośrednictwem PresentationHost. exe implementują ten interfejs, aby zapewnić punkt integracji między hostem a PresentationHost. exe.  
  
## <a name="remarks"></a>Uwagi  
 aplikacje [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)], takie jak przeglądarki sieci Web, mogą obsługiwać zawartość WPF, w tym [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] i luźny kod XAML. Aby hostować zawartość WPF, aplikacje [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] tworzą wystąpienie [kontrolki WebBrowser](https://go.microsoft.com/fwlink/?LinkId=97911). Aby można było hostować, WPF tworzy wystąpienie programu PresentationHost. exe, które udostępnia hostowaną zawartość WPF do hosta na potrzeby wyświetlania w [kontrolce WebBrowser](https://go.microsoft.com/fwlink/?LinkId=97911).  
  
 Integracja włączona przez `IWpfHostSupport` umożliwia programowi PresentationHost. exe:  
  
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
