---
title: Zagadnienia dotyczące współdziałania Direct3D9 i WPF
ms.date: 03/30/2017
helpviewer_keywords:
- WPF [WPF], Direct3D9 interop performance
- Direct3D9 [WPF interoperability], performance
ms.assetid: ea8baf91-12fe-4b44-ac4d-477110ab14dd
ms.openlocfilehash: 02a91c1824c5d6374f37b0af66a3308d33210c4a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932494"
---
# <a name="performance-considerations-for-direct3d9-and-wpf-interoperability"></a>Zagadnienia dotyczące współdziałania Direct3D9 i WPF
Zawartość Direct3D9 można hostować przy użyciu <xref:System.Windows.Interop.D3DImage> klasy. Hosting zawartości Direct3D9 może mieć wpływ na wydajność aplikacji. W tym temacie opisano najlepsze rozwiązania w celu zoptymalizowania wydajności podczas hostowania zawartości Direct3D9 w aplikacji Windows Presentation Foundation (WPF). W przypadku korzystania z systemu Windows Vista <xref:System.Windows.Interop.D3DImage> , Windows XP i ekranów z obsługą kilku monitorów te najlepsze rozwiązania obejmują używanie i najlepsze rozwiązania.  
  
> [!NOTE]
> Przykłady kodu, które przedstawiają te najlepsze rozwiązania, można znaleźć w temacie [WPF i Direct3D9](wpf-and-direct3d9-interoperation.md).  
  
## <a name="use-d3dimage-sparingly"></a>Używaj D3DImage oszczędnie  
 Zawartość Direct3D9 hostowana w <xref:System.Windows.Interop.D3DImage> wystąpieniu nie jest renderowana tak szybko jak w przypadku czystej aplikacji Direct3D. Kopiowanie powierzchni i opróżnianie bufora poleceń może być kosztowne. Wraz ze wzrostem <xref:System.Windows.Interop.D3DImage> liczby wystąpień występuje więcej wartości opróżniania i spadek wydajności. W związku z tym należy <xref:System.Windows.Interop.D3DImage> używać oszczędnie.  
  
## <a name="best-practices-on-windows-vista"></a>Najlepsze rozwiązania w systemie Windows Vista  
 Aby uzyskać najlepszą wydajność w systemie Windows Vista z wyświetlaczem skonfigurowanym do korzystania z modelu Windows Display Driver Model (WDDM), Utwórz powierzchnię Direct3D9 na `IDirect3DDevice9Ex` urządzeniu. Pozwala to na udostępnianie powierzchni. Karta wideo musi obsługiwać `D3DDEVCAPS2_CAN_STRETCHRECT_FROM_TEXTURES` funkcje i `D3DCAPS2_CANSHARERESOURCE` sterowniki w systemie Windows Vista. Wszystkie inne ustawienia powodują, że powierzchnia jest kopiowana za pomocą oprogramowania, co zmniejsza wydajność znacznie.  
  
> [!NOTE]
> Jeśli system Windows Vista ma wyświetlacz skonfigurowany do korzystania z modelu sterownika wyświetlania systemu Windows XP (XDDM), powierzchnia jest zawsze kopiowana za pomocą oprogramowania, niezależnie od ustawień. Przy użyciu odpowiednich ustawień i karty wideo w systemie Windows Vista będzie wyświetlana lepsza wydajność, ponieważ na sprzęcie są wykonywane kopie powierzchniowe.  
  
## <a name="best-practices-on-windows-xp"></a>Najlepsze rozwiązania w systemie Windows XP  
 Aby uzyskać najlepszą wydajność w systemie Windows XP, który korzysta z modelu sterownika wyświetlania systemu Windows XP (XDDM), Utwórz wyznaczoną dla siebie powierzchnię, `IDirect3DSurface9::GetDC` która zachowuje się prawidłowo po wywołaniu metody. `BitBlt` Wewnętrznie metoda transferuje powierzchnię między urządzeniami sprzętowymi. `GetDC` Metoda zawsze działa na powierzchniach XRGB. Jeśli jednak na komputerze klienckim jest uruchomiony system Windows XP z dodatkiem SP3 lub SP2, a w przypadku klienta jest również dostępna poprawka dla funkcji okna warstwowego, ta metoda działa tylko na powierzchniach ARGB. Karta wideo musi obsługiwać `D3DDEVCAPS2_CAN_STRETCHRECT_FROM_TEXTURES` funkcję sterownika.  
  
 16-bitowa głębokość wyświetlania pulpitu może znacząco obniżyć wydajność. Zalecany jest pulpit 32-bitowy.  
  
 W przypadku tworzenia aplikacji dla systemów Windows Vista i Windows XP Przetestuj wydajność w systemie Windows XP. Brak pamięci wideo w systemie Windows XP jest problemem. Ponadto <xref:System.Windows.Interop.D3DImage> w systemie Windows XP zużywa więcej pamięci wideo i przepustowości niż system Windows Vista WDDM ze względu na niezbędną dodatkową kopię pamięci wideo. W związku z tym można oczekiwać, że wydajność w systemie Windows XP niż w systemie Windows Vista jest niższa dla tego samego sprzętu wideo.  
  
> [!NOTE]
> XDDM jest dostępny zarówno w systemie Windows XP, jak i Windows Vista; jednak WDDM jest dostępny tylko w systemie Windows Vista.  
  
## <a name="general-best-practices"></a>Ogólne najlepsze rozwiązania  
 Podczas tworzenia urządzenia należy użyć `D3DCREATE_MULTITHREADED` flagi tworzenia. Zmniejsza to wydajność, ale system renderowania WPF wywołuje metody na tym urządzeniu z innego wątku. Upewnij się, że poprawnie przestrzegasz protokołu blokowania, tak aby żadne dwa wątki nie miały jednocześnie dostępu do urządzenia.  
  
 Jeśli renderowanie jest wykonywane w wątku zarządzanym WPF, zdecydowanie zaleca się utworzenie urządzenia przy użyciu `D3DCREATE_FPU_PRESERVE` flagi tworzenia. Bez tego ustawienia renderowanie D3D może zmniejszyć dokładność operacji podwójnej precyzji WPF i wprowadzić problemy z renderowaniem.  
  
 Rozmieszczanie <xref:System.Windows.Interop.D3DImage> a jest szybkie, chyba że utworzysz powierzchnię niepow2ą bez obsługi sprzętu lub na <xref:System.Windows.Media.DrawingBrush> kafelku lub <xref:System.Windows.Media.VisualBrush> , który zawiera <xref:System.Windows.Interop.D3DImage>.  
  
## <a name="best-practices-for-multi-monitor-displays"></a>Najlepsze rozwiązania dotyczące wyświetlania z obsługą kilku monitorów  
 Jeśli używasz komputera z wieloma monitorami, należy postępować zgodnie z wcześniej opisanymi najlepszymi rozwiązaniami. Istnieją także pewne dodatkowe zagadnienia dotyczące wydajności konfiguracji z obsługą kilku monitorów.  
  
 Po utworzeniu buforu zapasowego jest tworzony na określonym urządzeniu i na karcie, ale w przypadku każdej karty WPF może być wyświetlany bufor przedni. Kopiowanie między kartami w celu zaktualizowania buforu przedniego może być bardzo kosztowne. W systemie Windows Vista skonfigurowanym do korzystania z WDDM z wieloma kartami wideo i z `IDirect3DDevice9Ex` urządzeniem, jeśli bufor przedni znajduje się na innej karcie, ale nadal ma tę samą kartę wideo, nie ma żadnego poziomu wydajności. Jednak w systemach Windows XP i XDDM z wieloma kartami wideo istnieje znaczny spadek wydajności, gdy bufor przedni jest wyświetlany na innej karcie niż bufor zapasowy. Aby uzyskać więcej informacji, zobacz [WPF i Direct3D9](wpf-and-direct3d9-interoperation.md).  
  
## <a name="performance-summary"></a>Podsumowanie wydajności  
 W poniższej tabeli przedstawiono wydajność aktualizacji buforu przedniego jako funkcja systemu operacyjnego, formatu pikseli i blokady powierzchni. Bufor przedni i bufor zapasowy są zakładane na tej samej karcie. W zależności od konfiguracji karty aktualizacje sprzętu są zwykle znacznie szybsze niż aktualizacje oprogramowania.  
  
|Format pikseli powierzchni|Windows Vista, WDDM i 9Ex|Inne konfiguracje systemu Windows Vista|Windows XP z dodatkiem SP3 lub SP2 z poprawkami|Windows XP z dodatkiem SP2|  
|--------------------------|---------------------------------|----------------------------------------|--------------------------------------|--------------------|  
|D3DFMT_X8R8G8B8 (niezamykane)|**Aktualizacja sprzętowa**|Aktualizacja oprogramowania|Aktualizacja oprogramowania|Aktualizacja oprogramowania|  
|D3DFMT_X8R8G8B8 (zamykane)|**Aktualizacja sprzętowa**|Aktualizacja oprogramowania|**Aktualizacja sprzętowa**|**Aktualizacja sprzętowa**|  
|D3DFMT_A8R8G8B8 (niezamykane)|**Aktualizacja sprzętowa**|Aktualizacja oprogramowania|Aktualizacja oprogramowania|Aktualizacja oprogramowania|  
|D3DFMT_A8R8G8B8 (zamykane)|**Aktualizacja sprzętowa**|Aktualizacja oprogramowania|**Aktualizacja sprzętowa**|Aktualizacja oprogramowania|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Interop.D3DImage>
- [WPF i Direct3D9 — współdziałanie](wpf-and-direct3d9-interoperation.md)
- [Przewodnik: Tworzenie zawartości Direct3D9 dla hostingu w WPF](walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md)
- [Przewodnik: Hostowanie zawartości Direct3D9 w WPF](walkthrough-hosting-direct3d9-content-in-wpf.md)
