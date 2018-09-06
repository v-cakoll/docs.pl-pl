---
title: Używanie działań proceduralnych
ms.date: 03/30/2017
ms.assetid: 1c67f739-3878-48ad-806c-b2ce0d6733a0
ms.openlocfilehash: bd83f1a0fa9f3af7c22cee73fbc4f984a9ebf53c
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43804777"
---
# <a name="using-procedural-activities"></a>Używanie działań proceduralnych
W przykładzie użyto <xref:System.Activities.Statements.Sequence>, <xref:System.Activities.Statements.Assign>, <xref:System.Activities.Statements.If>, <xref:System.Activities.Statements.While>, <xref:System.Activities.Statements.Switch%601>, <xref:System.Activities.Statements.TryCatch>, i <xref:System.Activities.Statements.WriteLine> działania, aby zaimplementować zgadywania gier. Odgadnięcia gier wybiera losową liczbę, a gracz musi odgadnięcia tę liczbę. Gdy gracz wyśle nieprawidłowy wynik, przepływ pracy stanowi wskazówkę czy odgadnięcia wyższy lub niższy. Jeśli gracz próby odgadnięcia numer w przypadku prób ataków mniej niż 7, Gratulujemy specjalne jest wyświetlany użytkownikowi.  
  
## <a name="custom-activities-in-this-sample"></a>Niestandardowe działania w tym przykładzie  
  
### <a name="readline"></a>ReadLine  
 Odczytuje wiersz tekstu z konsoli. To działanie jest pochodną <xref:System.Activities.NativeActivity> klasy i tworzy zakładki, która zostanie wznowione przez aplikację konsoli, jeśli wiersz jest do odczytu.  
  
### <a name="promptint"></a>PromptInt  
 Monituje użytkownika o wpisanie liczby w, a następnie odczytuje z okna konsoli. Działanie jest pochodną <xref:System.Activities.Activity%601> i używa <xref:System.Activities.Statements.WriteLine> i `ReadLine` działań.  
  
##### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Za pomocą [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania GuessingGame.sln.  
  
2.  Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.  
  
3.  Aby uruchomić rozwiązanie, naciśnij kombinację klawiszy CTRL + F5.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Procedurals`