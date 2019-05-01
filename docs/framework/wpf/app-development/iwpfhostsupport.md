---
title: IWpfHostSupport
ms.date: 03/30/2017
helpviewer_keywords:
- IWpfHostSupport interface [WPF]
ms.assetid: cc5a0281-de81-4cc1-87e4-0e46b1a811e9
ms.openlocfilehash: 074167111b78edc517dda019465260d0acd54737
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62006697"
---
# <a name="iwpfhostsupport"></a>IWpfHostSupport
Aplikacje obsługujące [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zawartości za pośrednictwem PresentationHost.exe implementować ten interfejs zapewnia punkt integracji między hostem a PresentationHost.exe.  
  
## <a name="remarks"></a>Uwagi  
 [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] aplikacje, takie jak przeglądarki sieci Web może obsługiwać [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] zawartości, w tym [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] i luźno XAML. Na hoście [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] zawartości, [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] aplikacji Utwórz wystąpienie obiektu [formantu WebBrowser](https://go.microsoft.com/fwlink/?LinkId=97911). Będzie hostowana [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] tworzy wystąpienie PresentationHost.exe, co zapewnia hostowanej [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] zawartości do hosta w celu wyświetlania w [formantu WebBrowser](https://go.microsoft.com/fwlink/?LinkId=97911).  
  
 Integracja włączane przez `IWpfHostSupport` umożliwia PresentationHost.exe do:  
  
- Odnajdywanie i rejestrowanie w usłudze nieprzetworzonych danych wejściowych (urządzenia ludzi interfejs), które jest zainteresowany aplikacji hosta.  
  
- Komunikaty wejściowe z pierwotnych danych wejściowych zarejestrowanych i przekazywania wiadomości w odpowiedniej aplikacji hosta.  
  
- Wyślij zapytanie do aplikacji hosta dla niestandardowych interfejsów użytkownika postępu i błędów.  
  
> [!NOTE]
>  Ten interfejs API jest tylko przeznaczone i obsługiwane do użytku na komputerze klienckim lokalne  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|[GetRawInputDevices](getrawinputdevices.md)|Umożliwia PresentationHost.exe odnajdywania nieprzetworzonych danych wejściowych (urządzenia ludzi interfejs), które jest zainteresowany aplikacji hosta.|  
|[FilterInputMessage](filterinputmessage.md)|Metoda wywoływana przez PresentationHost.exe zawsze wtedy, gdy wiadomość zostaje odebrana, chyba że E_NOTIMPL jest zwracana.|  
|[GetCustomUI](getcustomui.md)|Domyślnie PresentationHost.exe zawiera swój własny postęp wdrażania i Błąd wdrażania interfejsów użytkownika, które są wyświetlane podczas wdrażania zawartości WPF.|
