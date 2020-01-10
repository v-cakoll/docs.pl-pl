---
title: IWpfHostSupport
ms.date: 03/30/2017
helpviewer_keywords:
- IWpfHostSupport interface [WPF]
ms.assetid: cc5a0281-de81-4cc1-87e4-0e46b1a811e9
ms.openlocfilehash: 4855fae2954e5650d8c9bbb81153ebe64249a867
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740191"
---
# <a name="iwpfhostsupport"></a>IWpfHostSupport
Aplikacje, które hostuje [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zawartość za pomocą PresentationHost. exe implementują ten interfejs, aby zapewnić punkt integracji między hostem a PresentationHost. exe.  
  
## <a name="remarks"></a>Uwagi  
 Aplikacje systemu Win32, takie jak przeglądarki sieci Web, mogą obsługiwać zawartość WPF, w tym aplikacje przeglądarki XAML (XBAP) i luźny kod XAML. Aby hostować zawartość WPF, aplikacje Win32 tworzą wystąpienie [kontrolki WebBrowser](https://go.microsoft.com/fwlink/?LinkId=97911). Aby można było hostować, WPF tworzy wystąpienie programu PresentationHost. exe, które udostępnia hostowaną zawartość WPF do hosta na potrzeby wyświetlania w [kontrolce WebBrowser](https://go.microsoft.com/fwlink/?LinkId=97911).  
  
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
|[FilterInputMessage](filterinputmessage.md)|Wywoływana przez PresentationHost. exe za każdym razem, gdy komunikat zostanie odebrany, chyba że E_NOTIMPL jest zwracana.|  
|[GetCustomUI](getcustomui.md)|Domyślnie program PresentationHost. exe udostępnia swój własny postęp wdrażania i interfejsy użytkownika błędów wdrażania, które są wyświetlane podczas wdrażania zawartości WPF.|
