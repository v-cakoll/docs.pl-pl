---
title: Zagadnienia dotyczące współdziałania Direct3D9 i WPF
ms.date: 03/30/2017
helpviewer_keywords:
- WPF [WPF], Direct3D9 interop performance
- Direct3D9 [WPF interoperability], performance
ms.assetid: ea8baf91-12fe-4b44-ac4d-477110ab14dd
ms.openlocfilehash: fd3c99f22a1d097c82494ba6eff344820162ed87
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57356731"
---
# <a name="performance-considerations-for-direct3d9-and-wpf-interoperability"></a>Zagadnienia dotyczące współdziałania Direct3D9 i WPF
Może obsługiwać zawartości Direct3D9 przy użyciu <xref:System.Windows.Interop.D3DImage> klasy. Hosting zawartości Direct3D9 może mieć wpływ na wydajność aplikacji. W tym temacie opisano najlepsze rozwiązania w celu zoptymalizowania wydajności, gdy hosting zawartości Direct3D9 w aplikacji Windows Presentation Foundation (WPF). Te najlepsze rozwiązania obejmują sposób używania <xref:System.Windows.Interop.D3DImage> i najlepsze rozwiązania, gdy używasz Windows Vista, Windows XP, i wyświetla wielu monitorów.  
  
> [!NOTE]
>  Aby uzyskać przykłady kodu, które pokazują tych najlepszych rozwiązań, zobacz [WPF i Direct3D9 — współdziałanie](wpf-and-direct3d9-interoperation.md).  
  
## <a name="use-d3dimage-sparingly"></a>Użyj D3DImage oszczędnie  
 Zawartości Direct3D9 hostowanych w <xref:System.Windows.Interop.D3DImage> wystąpienia nie jest renderowana jako wysoka jak w przypadku czystego aplikacji Direct3D. Kopiowanie powierzchni i opróżnianie buforu polecenia mogą być kosztowne operacje. Jako liczba <xref:System.Windows.Interop.D3DImage> zwiększa wystąpień opróżniania więcej występuje i spadku wydajności. Dlatego należy używać <xref:System.Windows.Interop.D3DImage> rzadko.  
  
## <a name="best-practices-on-windows-vista"></a>Najlepsze rozwiązania w systemie Windows Vista  
 Uzyskać najlepszą wydajność w Windows Vista, za pomocą wyświetlacza, który jest skonfigurowany do używania modelu wyświetlić Driver Windows (WDDM), utworzyć Twoje powierzchni Direct3D9 na `IDirect3DDevice9Ex` urządzenia. Dzięki temu udostępnianie powierzchni. Karta wideo musi obsługiwać `D3DDEVCAPS2_CAN_STRETCHRECT_FROM_TEXTURES` i `D3DCAPS2_CANSHARERESOURCE` możliwości sterowników w systemie Windows Vista. Inne ustawienia powodują powierzchni ma być kopiowany przy użyciu oprogramowania, co znacznie zmniejsza wydajność.  
  
> [!NOTE]
>  Jeśli ekran, który jest skonfigurowany do używania Windows XP wyświetlanie sterowników modelu (XDDM), Windows Vista powierzchni zawsze jest kopiowana za pośrednictwem oprogramowania niezależnie od ustawień. Za pomocą odpowiednich ustawień i karty wideo zobaczysz lepszą wydajność w Windows Vista korzystania WDDM, ponieważ kopie powierzchni są wykonywane w sprzęcie.  
  
## <a name="best-practices-on-windows-xp"></a>Najlepsze rozwiązania dotyczące Windows XP  
 Aby uzyskać najlepszą wydajność, Windows XP, który używa zestawu Windows XP wyświetlania sterownik modelu (XDDM), utworzyć powierzchni zamykane, który zachowuje się prawidłowo po `IDirect3DSurface9::GetDC` metoda jest wywoływana. Wewnętrznie `BitBlt` metoda przesyła powierzchni na urządzeniach sprzętowych. `GetDC` Metoda zawsze działa na powierzchniach XRGB. Jednakże, jeśli komputer kliencki jest systemem Windows XP z dodatkiem SP3 lub SP2 i klient ma również poprawka dla funkcji okno z warstwami, ta metoda działa tylko na powierzchniach ARGB. Karta wideo musi obsługiwać `D3DDEVCAPS2_CAN_STRETCHRECT_FROM_TEXTURES` możliwości sterownika.  
  
 Głębokość 16-bitowych ekranu mogą znacznie zmniejszyć wydajność. 32-bitowy komputer stacjonarny jest zalecane.  
  
 Jeśli tworzysz dla Windows Vista i Windows XP, należy przetestować wydajność na Windows XP. Wyczerpaniu pamięci wideo w systemie Windows XP jest istotna. Ponadto <xref:System.Windows.Interop.D3DImage> Windows XP używa więcej pamięci wideo, a przepustowość niż Windows Vista WDDM, ze względu na potrzeby kopiowania dodatkowych filmów wideo pamięci. W związku z tym można oczekiwać, że wydajność za co gorsza, Windows XP, niż w Windows Vista do tego samego sprzętu wideo.  
  
> [!NOTE]
>  XDDM jest dostępna zarówno Windows XP i Windows Vista; jednak WDDM jest dostępna tylko w systemie Windows Vista.  
  
## <a name="general-best-practices"></a>Najlepsze praktyki ogólne  
 Podczas tworzenia urządzenia użyć `D3DCREATE_MULTITHREADED` flagi tworzenia. Pozwala to zmniejszyć wydajność, ale system renderowania WPF wywołuje metody na tym urządzeniu z innego wątku. Należy postępować zgodnie blokowania protokołu poprawnie, tak aby żadne dwa wątki dostęp do urządzenia, w tym samym czasie.  
  
 Jeśli Twoje renderowania jest wykonywana w wątku, WPF, zarządzanych, zalecane jest utworzenie urządzenia przy użyciu `D3DCREATE_FPU_PRESERVE` flagi tworzenia. Bez tego ustawienia renderowania D3D może zmniejszyć dokładność operacje podwójnej precyzji WPF i powodować problemy z renderowaniem.  
  
 Budowanie kafelków <xref:System.Windows.Interop.D3DImage> jest szybkiego działania, chyba, że Kafelek powierzchnię bez pow2 bez obsługi sprzętowej, lub jeśli użytkownik Kafelek <xref:System.Windows.Media.DrawingBrush> lub <xref:System.Windows.Media.VisualBrush> zawierający <xref:System.Windows.Interop.D3DImage>.  
  
## <a name="best-practices-for-multi-monitor-displays"></a>Najlepsze rozwiązania dotyczące wielu monitorów  
 Jeśli używasz komputera, który ma wiele monitorów, należy przestrzegać opisany wcześniej najlepszych rozwiązań. Istnieją również pewne dodatkowe zagadnienia dotyczące konfiguracji wielu monitorów.  
  
 Podczas tworzenia buforu zapasowego jest tworzona na określonym urządzeniem i karty, ale frontonu buforu dla WPF mogą być wyświetlane na żadnej karcie. Kopiowanie między kart, aby zaktualizować frontonu buforu może być bardzo kosztowna. W Windows Vista, który jest skonfigurowany do używania WDDM z wielu kart wideo i `IDirect3DDevice9Ex` urządzenia, jeśli bufor frontonu znajduje się na inną kartę, ale mimo to ta sama karta wideo, nie ma żadnego pogorszenia wydajności. W systemie Windows XP i XDDM z wieloma kartami wideo, istnieje jednak spadek istotnie poprawiającą wydajność podczas pierwszej buforu jest wyświetlany na inną kartę niż buforu zapasowego. Aby uzyskać więcej informacji, zobacz [WPF i Direct3D9 — współdziałanie](wpf-and-direct3d9-interoperation.md).  
  
## <a name="performance-summary"></a>Podsumowanie wydajności  
 W poniższej tabeli przedstawiono wydajność aktualizację usługi buffer frontonu w zależności od systemu operacyjnego, format pikseli i lockability powierzchni. Bufor przód i Wstecz bufor są zakłada się, że na tej samej karcie. W zależności od konfiguracji karty aktualizacje sprzętu są zazwyczaj znacznie szybsze niż aktualizacji oprogramowania.  
  
|Format pikseli urządzenia Surface|Windows Vista, WDDM i 9Ex|Inne konfiguracje, Windows Vista|Windows XP z dodatkiem SP3 lub SP2 z poprawek|Windows XP z dodatkiem SP2|  
|--------------------------|---------------------------------|----------------------------------------|--------------------------------------|--------------------|  
|D3DFMT_X8R8G8B8 (nie zamykane)|**Aktualizacja sprzętu**|Aktualizacja oprogramowania|Aktualizacja oprogramowania|Aktualizacja oprogramowania|  
|D3DFMT_X8R8G8B8 (lockable)|**Aktualizacja sprzętu**|Aktualizacja oprogramowania|**Aktualizacja sprzętu**|**Aktualizacja sprzętu**|  
|D3DFMT_A8R8G8B8 (nie zamykane)|**Aktualizacja sprzętu**|Aktualizacja oprogramowania|Aktualizacja oprogramowania|Aktualizacja oprogramowania|  
|D3DFMT_A8R8G8B8 (lockable)|**Aktualizacja sprzętu**|Aktualizacja oprogramowania|**Aktualizacja sprzętu**|Aktualizacja oprogramowania|  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Interop.D3DImage>
- [WPF i Direct3D9 — współdziałanie](wpf-and-direct3d9-interoperation.md)
- [Przewodnik: Tworzenie zawartości Direct3D9 dla hostingu w WPF](walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md)
- [Przewodnik: Hosting zawartości Direct3D9 w WPF](walkthrough-hosting-direct3d9-content-in-wpf.md)
