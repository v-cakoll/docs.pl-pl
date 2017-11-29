---
title: "Jak użyć wyzwalaczy zdarzeń, aby kontrolować scenorys po uruchomieniu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- triggers [WPF], controlling Storyboards
- event triggers [WPF], controlling Storyboards
- Storyboards [WPF], controlling after start
ms.assetid: 3b115594-6a93-4972-b24d-61aa16f1c15f
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7d9e096969713cc4b9c42261b238691d51cb49d9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-event-triggers-to-control-a-storyboard-after-it-starts"></a>Jak użyć wyzwalaczy zdarzeń, aby kontrolować scenorys po uruchomieniu
W tym przykładzie przedstawiono sposób kontrolowania <xref:System.Windows.Media.Animation.Storyboard> po jego uruchomieniu. Aby uruchomić <xref:System.Windows.Media.Animation.Storyboard> za pomocą [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], użyj <xref:System.Windows.Media.Animation.BeginStoryboard>, która dystrybuuje animacje obiektów i właściwości animacji i następnie uruchamia scenorysu. Jeśli zostanie nadana <xref:System.Windows.Media.Animation.BeginStoryboard> nazwę przez określenie jego <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> właściwości, można ustawić, którymi można sterować scenorysu. Użytkownik może interakcyjnie wybrać scenorysu po jego uruchomieniu.  
  
 Użyj następujących akcji scenorysu razem z <xref:System.Windows.EventTrigger> obiekty do kontrolowania scenorysu.  
  
-   <xref:System.Windows.Media.Animation.PauseStoryboard>: Wstrzymuje scenorysu.  
  
-   <xref:System.Windows.Media.Animation.ResumeStoryboard>: Wznawia działanie wstrzymanej scenorysu.  
  
-   <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: Zmienia szybkość scenorysu.  
  
-   <xref:System.Windows.Media.Animation.SkipStoryboardToFill>: Przesuwa scenorysu do końca okresu, jeśli istnieje.  
  
-   <xref:System.Windows.Media.Animation.StopStoryboard>: Przestaje scenorysu.  
  
-   <xref:System.Windows.Media.Animation.RemoveStoryboard>: Usuwa scenorysu, zwolnić zasoby.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto akcji sterowane scenorysu do sterowania interaktywnego scenorysu.  
  
 **Uwaga:** Aby zapoznać się przykładem kontrolowanie scenorysu przy użyciu kodu, zobacz [kontrolować scenorysu po jego rozpoczyna się za pomocą jego interakcyjne metod](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-storyboard-after-it-starts.md).  
  
 [!code-xaml[timingbehaviors_snip#ControlStoryboardExampleUsingWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/ControlStoryboardExample.xaml#controlstoryboardexampleusingwholepage)]  
  
 Aby uzyskać dodatkowe przykłady, zobacz [galerii przykład animacji](http://go.microsoft.com/fwlink/?LinkID=159969).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.Animation.ResumeStoryboard>  
 <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>  
 <xref:System.Windows.Media.Animation.SkipStoryboardToFill>  
 <xref:System.Windows.Media.Animation.PauseStoryboard>  
 <xref:System.Windows.Media.Animation.StopStoryboard>  
 <xref:System.Windows.Media.Animation.SeekStoryboard>  
 [Kontrolowanie scenorysu po uruchomieniu, za pomocą jej metod interakcyjne](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-storyboard-after-it-starts.md)  
 [Animacja — omówienie](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Scenorys — omówienie](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
