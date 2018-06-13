---
title: Zagadnienia dotyczące współdziałania Direct3D9 i WPF
ms.date: 03/30/2017
helpviewer_keywords:
- WPF [WPF], Direct3D9 interop performance
- Direct3D9 [WPF interoperability], performance
ms.assetid: ea8baf91-12fe-4b44-ac4d-477110ab14dd
ms.openlocfilehash: 52085579c2a432e7db1ebec096a931e0d51718f8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33549207"
---
# <a name="performance-considerations-for-direct3d9-and-wpf-interoperability"></a>Zagadnienia dotyczące współdziałania Direct3D9 i WPF
Zawartość Direct3D9 można obsługiwać przy użyciu <xref:System.Windows.Interop.D3DImage> klasy. Hostowanie zawartości Direct3D9 mogą wpływać na wydajność aplikacji. W tym temacie opisano najlepsze rozwiązania w celu optymalizacji wydajności, odnośnie do hostowania zawartości Direct3D9 w aplikacji Windows Presentation Foundation (WPF). Sposób użycia obejmują następujące najlepsze rozwiązania <xref:System.Windows.Interop.D3DImage> i najlepsze rozwiązania w przypadku, gdy używasz systemu Windows Vista, Windows XP i wielu monitor wyświetla.  
  
> [!NOTE]
>  Aby uzyskać przykłady kodu, które przedstawiają następujące najlepsze rozwiązania, zobacz [WPF i współdziałanie Direct3D9](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md).  
  
## <a name="use-d3dimage-sparingly"></a>Użyj D3DImage oszczędnie  
 Direct3D9 zawartości hostowanej w <xref:System.Windows.Interop.D3DImage> wystąpienia nie jest renderowana jako wysoka jak w przypadku czysty aplikacji Direct3D. Kopiowanie powierzchni i opróżniania buforu polecenie może być kosztowne operacje. Jak liczba <xref:System.Windows.Interop.D3DImage> zwiększa wystąpień opróżniania więcej występuje i powoduje spadek wydajności. W związku z tym należy używać <xref:System.Windows.Interop.D3DImage> oszczędnie.  
  
## <a name="best-practices-on-windows-vista"></a>Najlepsze rozwiązania w systemie Windows Vista  
 Aby uzyskać najlepszą wydajność w systemie Windows Vista z wyświetlania, która jest skonfigurowana do używania modelu wyświetlić sterowników systemu Windows (WDDM), należy utworzyć obszar Direct3D9 na `IDirect3DDevice9Ex` urządzenia. Dzięki temu udostępnianie powierzchni. Karta wideo musi obsługiwać `D3DDEVCAPS2_CAN_STRETCHRECT_FROM_TEXTURES` i `D3DCAPS2_CANSHARERESOURCE` możliwości sterownika w systemie Windows Vista. Inne ustawienia powodują powierzchni do skopiowania przez oprogramowanie, które znacząco zmniejsza wydajność.  
  
> [!NOTE]
>  Jeśli system Windows Vista wyświetlania, która jest skonfigurowana do używania systemu Windows XP wyświetlić sterownik modelu (XDDM), powierzchni zawsze jest kopiowana za pośrednictwem oprogramowania, niezależnie od ustawień. Odpowiednie ustawienia i karty wideo zobaczysz lepszą wydajność w systemie Windows Vista używania WDDM, ponieważ powierzchni kopie są wykonywane w sprzęcie.  
  
## <a name="best-practices-on-windows-xp"></a>Najlepsze rozwiązania w systemie Windows XP  
 Aby uzyskać najlepszą wydajność w systemie Windows XP, który korzysta z systemu Windows XP wyświetlania sterownik modelu (XDDM), tworzenie zamykane powierzchni, która działa prawidłowo po `IDirect3DSurface9::GetDC` metoda jest wywoływana. Wewnętrznie `BitBlt` metody przesyła powierzchni na urządzeniach sprzętowych. `GetDC` Metoda zawsze działa na powierzchni XRGB. Jednak jeśli na komputerze klienckim jest zainstalowany system Windows XP z dodatkiem SP3 lub SP2, a klient ma również poprawka dla funkcji warstwie okno, ta metoda działa tylko na powierzchni ARGB. Karta wideo musi obsługiwać `D3DDEVCAPS2_CAN_STRETCHRECT_FROM_TEXTURES` możliwości sterownika.  
  
 Głębokość ekranu 16-bitowych może znacznie zmniejszyć wydajność. Zaleca się pulpitu 32-bitowych.  
  
 Jeśli tworzysz dla systemu Windows Vista i Windows XP, należy przetestować wydajność w systemie Windows XP. Wyczerpaniu pamięci wideo w systemie Windows XP jest problemem. Ponadto <xref:System.Windows.Interop.D3DImage> w systemie Windows XP używa więcej pamięci wideo i przepustowość niż Windows Vista WDDM ze względu na potrzeby kopiowania pamięci bardzo wideo. W związku z tym można spodziewać się wydajności być gorsza w systemie Windows XP niż w systemie Windows Vista dla tego samego sprzętu wideo.  
  
> [!NOTE]
>  XDDM jest dostępna na systemie Windows XP i Windows Vista; jednak WDDM jest dostępna tylko w systemie Windows Vista.  
  
## <a name="general-best-practices"></a>Najlepsze praktyki ogólne  
 Podczas tworzenia urządzenia, użyj `D3DCREATE_MULTITHREADED` flagi tworzenia. Pozwala to zmniejszyć wydajność, ale system renderowania WPF wywołuje metody dla tego urządzenia z innego wątku. Należy postępować zgodnie protokołu blokowania poprawnie, dzięki czemu nie ma dwa wątków dostępu do urządzenia, w tym samym czasie.  
  
 Jeśli Twoje renderowania jest wykonywana w wątku WPF zarządzane, zdecydowanie zaleca się utworzenie urządzenia w usłudze `D3DCREATE_FPU_PRESERVE` flagi tworzenia. Bez tego ustawienia renderowania D3D można zmniejszyć dokładność operacji podwójnej precyzji WPF i powodować problemy związane z renderowaniem.  
  
 Ustawianie widoku kafelków <xref:System.Windows.Interop.D3DImage> jest szybkie, chyba, że Kafelek powierzchni z systemem innym niż pow2 bez obsługi sprzętu lub jeśli użytkownik kafelka <xref:System.Windows.Media.DrawingBrush> lub <xref:System.Windows.Media.VisualBrush> zawierający <xref:System.Windows.Interop.D3DImage>.  
  
## <a name="best-practices-for-multi-monitor-displays"></a>Najlepsze rozwiązania dotyczące wielu monitorów  
 Jeśli używasz komputera, który ma wiele monitorów, należy wykonać opisane wcześniej najlepszych rozwiązań. Dostępne są także niektóre dodatkowe zagadnienia dotyczące wydajności związane wiele monitorów.  
  
 Podczas tworzenia buforu zapasowego jest tworzona na określonym urządzeniu i karty, ale WPF mogą być wyświetlane front buforu na wszystkich kart. Kopiowanie między kart, aby zaktualizować front buforu może być bardzo kosztowna. W systemie Windows Vista, który jest skonfigurowany do używania WDDM z wielu kart wideo i `IDirect3DDevice9Ex` urządzenia, jeśli bufor front jest na inną kartę, ale nadal tej samej karty wideo, nie ma wpływ na wydajność. W systemach Windows XP i XDDM z wielu kart wideo, istnieje jednak zmniejszenie wydajności znaczące po front bufor jest wyświetlany na inną kartę niż buforu zapasowego. Aby uzyskać więcej informacji, zobacz [WPF i współdziałanie Direct3D9](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md).  
  
## <a name="performance-summary"></a>Podsumowanie wydajności  
 W poniższej tabeli przedstawiono wydajności aktualizacji front buforu w zależności od systemu operacyjnego, format pikseli i lockability powierzchni. Front buforu i buforu zapasowego muszą być w tej samej karty. W zależności od konfiguracji karty aktualizacje sprzętu są zwykle dużo szybsze niż aktualizacji oprogramowania.  
  
|Format pikseli powierzchni|Windows Vista, WDDM i 9Ex|Inne konfiguracje systemu Windows Vista|Windows XP z dodatkiem SP3 lub SP2 z poprawek|Windows XP z dodatkiem SP2|  
|--------------------------|---------------------------------|----------------------------------------|--------------------------------------|--------------------|  
|D3DFMT_X8R8G8B8 (nie zamykane)|**Aktualizacja sprzętu**|Aktualizacja oprogramowania|Aktualizacja oprogramowania|Aktualizacja oprogramowania|  
|D3DFMT_X8R8G8B8 (zamykane)|**Aktualizacja sprzętu**|Aktualizacja oprogramowania|**Aktualizacja sprzętu**|**Aktualizacja sprzętu**|  
|D3DFMT_A8R8G8B8 (nie zamykane)|**Aktualizacja sprzętu**|Aktualizacja oprogramowania|Aktualizacja oprogramowania|Aktualizacja oprogramowania|  
|D3DFMT_A8R8G8B8 (zamykane)|**Aktualizacja sprzętu**|Aktualizacja oprogramowania|**Aktualizacja sprzętu**|Aktualizacja oprogramowania|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Interop.D3DImage>  
 [WPF i Direct3D9 — współdziałanie](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md)  
 [Przewodnik: tworzenie zawartości Direct3D9 dla hostingu w WPF](../../../../docs/framework/wpf/advanced/walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md)  
 [Przewodnik: hosting zawartości Direct3D9 w WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-direct3d9-content-in-wpf.md)
