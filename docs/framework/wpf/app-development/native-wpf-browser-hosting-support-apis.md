---
title: Interfejsy API obsługi hostingu natywnej przeglądarki
ms.date: 03/30/2017
f1_keywords:
- AutoGeneratedOrientationPage
helpviewer_keywords:
- browser hosting support [WPF]
- WPF browser hosting support APIs [WPF]
ms.assetid: 82c133a8-d760-45fb-a2b9-3a997537f1d4
ms.openlocfilehash: 514b93423ddb029413b6f7b05241cdde88a80fd4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186883"
---
# <a name="native-wpf-browser-hosting-support-apis"></a>Macierzysta przeglądarka WPF wsparcia API hostingu
Hosting aplikacji WPF w przeglądarkach sieci Web jest ułatwiony przez serwer aktywnego dokumentu (znany również jako DocObject) zarejestrowany z hosta WPF. Program Internet Explorer może bezpośrednio aktywować i zintegrować się z aktywnym dokumentem. Do hostingu XBAPs i luźnych dokumentów XAML w przeglądarkach Mozilla, WPF zapewnia wtyczkę NPAPI, która zapewnia podobne środowisko hostingowe do serwera WPF Active Document, jak internet explorer. Jednak najprostszym praktycznym sposobem hostowania dokumentów XBAPs i XAML w innych przeglądarkach i autonomicznych aplikacjach jest sterowanie przeglądarką internet explorer. Formant przeglądarki sieci Web udostępnia złożone środowisko hostingowe serwera aktywnych dokumentów, ale umożliwia własnemu hostowi dostosowywanie i rozszerzanie tego środowiska oraz bezpośrednią komunikację z bieżącym obiektem Active Document.  
  
 Serwer WPF Active Document implementuje kilka typowych interfejsów hostingowych, w tym [IOleObject](/windows/win32/api/oleidl/nn-oleidl-ioleobject), [IOleDocument](/windows/win32/api/docobj/nn-docobj-ioledocument), [IOleInPlaceActiveObject](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceactiveobject), [IPersistMoniker](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms775042(v=vs.85)), [IOleCommandTarget](/windows/win32/api/docobj/nn-docobj-iolecommandtarget). Po hostowania w formancie przeglądarki sieci Web, interfejsy te mogą być kwerendy z obiektu zwróconego przez [IWebBrowser2::Document](https://docs.microsoft.com/previous-versions/aa752116(v=vs.85)) właściwości.  
  
## <a name="iolecommandtarget"></a>Iolecommandtarget  
 Implementacja serwera WPF Active Document [iOleCommandTarget](/windows/win32/api/docobj/nn-docobj-iolecommandtarget) obsługuje liczne polecenia związane z nawigacją i specyficzne dla przeglądarki standardowej grupy poleceń OLE (z identyfikatorem GUID grupy poleceń null). Ponadto rozpoznaje niestandardową grupę poleceń o nazwie CGID_PresentationHost. Obecnie w tej grupie zdefiniowano tylko jedno polecenie.  
  
```cpp  
DEFINE_GUID(CGID_PresentationHost, 0xd0288c55, 0xd6, 0x4f5e, 0xa8, 0x51, 0x79, 0xde, 0xc5, 0x1b, 0x10, 0xec);  
enum PresentationHostCommands {
   PHCMDID_TABINTO = 1
};  
```  
  
 PHCMDID_TABINTO nakazuje PresentationHost, aby przełączyć fokus na pierwszy lub ostatni element focusable w jego zawartości, w zależności od stanu klawisza Shift.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [IEnumRAWINPUTDEVICE](ienumrawinputdevice.md)  
 [IWpfHostSupport](iwpfhostsupport.md)
