---
title: IWpfHostSupport
ms.date: 03/30/2017
helpviewer_keywords:
- IWpfHostSupport interface [WPF]
ms.assetid: cc5a0281-de81-4cc1-87e4-0e46b1a811e9
ms.openlocfilehash: 51964358d27a16d9840e29be06c11f57de2fad23
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33548197"
---
# <a name="iwpfhostsupport"></a>IWpfHostSupport
Aplikacje, które obsługują [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zawartości za pośrednictwem PresentationHost.exe implementuje ten interfejs zapewnia punkt integracji między hostem a PresentationHost.exe.  
  
## <a name="remarks"></a>Uwagi  
 [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] aplikacje, takie jak przeglądarki sieci Web mogą obsługiwać [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] zawartość, łącznie z [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] utrata XAML. Na hoście [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] zawartości, [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] aplikacji Utwórz wystąpienie [formant WebBrowser](http://go.microsoft.com/fwlink/?LinkId=97911). Ma być obsługiwana [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] tworzy wystąpienie PresentationHost.exe, która zapewnia hostowanej [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] zawartości do hosta do wyświetlenia w [formant WebBrowser](http://go.microsoft.com/fwlink/?LinkId=97911).  
  
 Integracja włączane przez `IWpfHostSupport` umożliwia PresentationHost.exe do:  
  
-   Odnajdź i zarejestruj z urządzeniami wejściowych surowego (człowieka interfejsu urządzenia), które jest zainteresowana aplikacji hosta.  
  
-   Komunikaty wejściowe z zarejestrowanego urządzenia wejściowe pierwotnych i przekazywania wiadomości odpowiednie do aplikacji hosta.  
  
-   Wyślij zapytanie do aplikacji hosta dla niestandardowych interfejsów użytkownika postępu i błędów.  
  
> [!NOTE]
>  Ten interfejs API jest tylko przeznaczone i obsługiwana na maszynie lokalnej klienta  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|[GetRawInputDevices](../../../../docs/framework/wpf/app-development/getrawinputdevices.md)|Umożliwia PresentationHost.exe w celu odnalezienia urządzeń wejściowych raw (człowieka interfejsu urządzenia), które jest zainteresowana aplikacji hosta.|  
|[FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md)|Metoda wywoływana przez PresentationHost.exe zawsze, gdy wiadomość zostanie odebrana, chyba że E_NOTIMPL jest zwracany.|  
|[GetCustomUI](../../../../docs/framework/wpf/app-development/getcustomui.md)|Domyślnie PresentationHost.exe zapewnia własne postępu wdrożenia i Błąd wdrażania interfejsów użytkownika, które są wyświetlane po wdrożeniu zawartości WPF.|
