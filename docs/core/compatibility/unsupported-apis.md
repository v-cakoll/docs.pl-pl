---
title: Nieobsługiwały interfejsy API w programie .NET Core
titleSuffix: ''
description: Dowiedz się, które interfejsy API z platformy .NET Framework, które zawsze zgłaszają wyjątek w programie .NET Core.
ms.date: 12/23/2019
ms.openlocfilehash: bd3516d9480ef42b6ea89825ba64867a3ca104e3
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242949"
---
# <a name="apis-that-always-throw-exceptions-on-net-core"></a><span data-ttu-id="68629-103">Interfejsy API, które zawsze zgłaszają wyjątki w programie .NET Core</span><span class="sxs-lookup"><span data-stu-id="68629-103">APIs that always throw exceptions on .NET Core</span></span>

<span data-ttu-id="68629-104">Następujące interfejsy API zawsze <xref:System.PlatformNotSupportedException> będą rzucać na .NET Core na wszystkich lub podzbiór platform.</span><span class="sxs-lookup"><span data-stu-id="68629-104">The following APIs will always throw a <xref:System.PlatformNotSupportedException> on .NET Core on all or a subset of platforms.</span></span>

<span data-ttu-id="68629-105">W tym artykule organizuje dotkniętych członków interfejsu API według obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="68629-105">This article organizes the affected API members by namespace.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="68629-106">Ten artykuł jest w toku.</span><span class="sxs-lookup"><span data-stu-id="68629-106">This article is a work-in-progress.</span></span> <span data-ttu-id="68629-107">Nie jest to pełna lista interfejsów API, które zgłaszają wyjątki w programie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="68629-107">It is not a complete list of APIs that throw exceptions on .NET Core.</span></span>
> - <span data-ttu-id="68629-108">Ten artykuł nie zawiera jawnych implementacji interfejsu dla serializacji binarnej, które są wrzucane na .NET Core.</span><span class="sxs-lookup"><span data-stu-id="68629-108">This article does not include the explicit interface implementations for binary serialization that throw on .NET Core.</span></span> <span data-ttu-id="68629-109">Aby uzyskać więcej informacji, zobacz [Serializacja binarna w .NET Core](../../standard/serialization/binary-serialization.md#net-core).</span><span class="sxs-lookup"><span data-stu-id="68629-109">For more information, see [Binary serialization in .NET Core](../../standard/serialization/binary-serialization.md#net-core).</span></span>

## <a name="system"></a><span data-ttu-id="68629-110">System</span><span class="sxs-lookup"><span data-stu-id="68629-110">System</span></span>

| <span data-ttu-id="68629-111">Członek</span><span class="sxs-lookup"><span data-stu-id="68629-111">Member</span></span> | <span data-ttu-id="68629-112">Platformy, które rzucają</span><span class="sxs-lookup"><span data-stu-id="68629-112">Platforms that throw</span></span> |
| - | - |
| <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> | <span data-ttu-id="68629-113">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-113">All</span></span> |
| <xref:System.AppDomain.ExecuteAssembly(System.String,System.String[],System.Byte[],System.Configuration.Assemblies.AssemblyHashAlgorithm)?displayProperty=nameWithType> | <span data-ttu-id="68629-114">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-114">All</span></span> |
| <xref:System.Console.CapsLock?displayProperty=nameWithType> | <span data-ttu-id="68629-115">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="68629-115">Linux and macOS</span></span> |
| <xref:System.Console.NumberLock?displayProperty=nameWithType> | <span data-ttu-id="68629-116">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="68629-116">Linux and macOS</span></span> |
| <xref:System.Delegate.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="68629-117">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-117">All</span></span> |
| <xref:System.Exception.SerializeObjectState?displayProperty=nameWithType> | <span data-ttu-id="68629-118">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-118">All</span></span> |
| <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="68629-119">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-119">All</span></span> |
| <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="68629-120">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-120">All</span></span> |
| <xref:System.OperatingSystem.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="68629-121">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-121">All</span></span> |
| <xref:System.Type.ReflectionOnlyGetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="68629-122">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-122">All</span></span> |

## <a name="systemcodedomcompiler"></a><span data-ttu-id="68629-123">System.CodeDom.Compiler</span><span class="sxs-lookup"><span data-stu-id="68629-123">System.CodeDom.Compiler</span></span>

| <span data-ttu-id="68629-124">Członek</span><span class="sxs-lookup"><span data-stu-id="68629-124">Member</span></span> | <span data-ttu-id="68629-125">Platformy, które rzucają</span><span class="sxs-lookup"><span data-stu-id="68629-125">Platforms that throw</span></span> |
| - | - |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A?displayProperty=nameWithType> | <span data-ttu-id="68629-126">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-126">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A?displayProperty=nameWithType> | <span data-ttu-id="68629-127">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-127">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A?displayProperty=nameWithType> | <span data-ttu-id="68629-128">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-128">All</span></span> |

## <a name="systemcollectionsspecialized"></a><span data-ttu-id="68629-129">System.collections.specialized</span><span class="sxs-lookup"><span data-stu-id="68629-129">System.Collections.Specialized</span></span>

| <span data-ttu-id="68629-130">Członek</span><span class="sxs-lookup"><span data-stu-id="68629-130">Member</span></span> | <span data-ttu-id="68629-131">Platformy, które rzucają</span><span class="sxs-lookup"><span data-stu-id="68629-131">Platforms that throw</span></span> |
| - | - |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="68629-132">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-132">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="68629-133">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-133">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="68629-134">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-134">All</span></span> |

## <a name="systemconfiguration"></a><span data-ttu-id="68629-135">System.configuration</span><span class="sxs-lookup"><span data-stu-id="68629-135">System.Configuration</span></span>

| <span data-ttu-id="68629-136">Członek</span><span class="sxs-lookup"><span data-stu-id="68629-136">Member</span></span> | <span data-ttu-id="68629-137">Platformy, które rzucają</span><span class="sxs-lookup"><span data-stu-id="68629-137">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="68629-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType>(wszyscy członkowie)</span><span class="sxs-lookup"><span data-stu-id="68629-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (all members)</span></span> | <span data-ttu-id="68629-139">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-139">All</span></span> |

## <a name="systemconsole"></a><span data-ttu-id="68629-140">System.console</span><span class="sxs-lookup"><span data-stu-id="68629-140">System.Console</span></span>

| <span data-ttu-id="68629-141">Członek</span><span class="sxs-lookup"><span data-stu-id="68629-141">Member</span></span> | <span data-ttu-id="68629-142">Platformy, które rzucają</span><span class="sxs-lookup"><span data-stu-id="68629-142">Platforms that throw</span></span> |
| - | - |
| <xref:System.Console.Beep?displayProperty=nameWithType> | <span data-ttu-id="68629-143">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="68629-143">Linux and macOS</span></span> |
| <span data-ttu-id="68629-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType>(tylko zestaw)</span><span class="sxs-lookup"><span data-stu-id="68629-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="68629-145">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="68629-145">Linux and macOS</span></span> |
| <span data-ttu-id="68629-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType>(tylko zestaw)</span><span class="sxs-lookup"><span data-stu-id="68629-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="68629-147">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="68629-147">Linux and macOS</span></span> |
| <span data-ttu-id="68629-148"><xref:System.Console.CursorSize?displayProperty=nameWithType>(tylko zestaw)</span><span class="sxs-lookup"><span data-stu-id="68629-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="68629-149">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="68629-149">Linux and macOS</span></span> |
| <span data-ttu-id="68629-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType>(tylko dostać)</span><span class="sxs-lookup"><span data-stu-id="68629-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="68629-151">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="68629-151">Linux and macOS</span></span> |
| <xref:System.Console.MoveBufferArea%2A?displayProperty=nameWithType> | <span data-ttu-id="68629-152">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="68629-152">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowPosition%2A?displayProperty=nameWithType> | <span data-ttu-id="68629-153">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="68629-153">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowSize%2A?displayProperty=nameWithType> | <span data-ttu-id="68629-154">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="68629-154">Linux and macOS</span></span> |
| <span data-ttu-id="68629-155"><xref:System.Console.Title?displayProperty=nameWithType>(tylko dostać)</span><span class="sxs-lookup"><span data-stu-id="68629-155"><xref:System.Console.Title?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="68629-156">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="68629-156">Linux and macOS</span></span> |
| <span data-ttu-id="68629-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType>(tylko zestaw)</span><span class="sxs-lookup"><span data-stu-id="68629-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="68629-158">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="68629-158">Linux and macOS</span></span> |
| <span data-ttu-id="68629-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType>(tylko zestaw)</span><span class="sxs-lookup"><span data-stu-id="68629-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="68629-160">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="68629-160">Linux and macOS</span></span> |
| <span data-ttu-id="68629-161"><xref:System.Console.WindowTop?displayProperty=nameWithType>(tylko zestaw)</span><span class="sxs-lookup"><span data-stu-id="68629-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="68629-162">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="68629-162">Linux and macOS</span></span> |
| <span data-ttu-id="68629-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType>(tylko zestaw)</span><span class="sxs-lookup"><span data-stu-id="68629-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="68629-164">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="68629-164">Linux and macOS</span></span> |

## <a name="systemdatacommon"></a><span data-ttu-id="68629-165">System.Data.Common</span><span class="sxs-lookup"><span data-stu-id="68629-165">System.Data.Common</span></span>

| <span data-ttu-id="68629-166">Członek</span><span class="sxs-lookup"><span data-stu-id="68629-166">Member</span></span> | <span data-ttu-id="68629-167">Platformy, które rzucają</span><span class="sxs-lookup"><span data-stu-id="68629-167">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="68629-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType>(rzuty) <xref:System.NotSupportedException></span><span class="sxs-lookup"><span data-stu-id="68629-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (throws <xref:System.NotSupportedException>)</span></span> | <span data-ttu-id="68629-169">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-169">All</span></span> |

## <a name="systemdiagnosticsprocess"></a><span data-ttu-id="68629-170">System.Diagnostics.Process</span><span class="sxs-lookup"><span data-stu-id="68629-170">System.Diagnostics.Process</span></span>

| <span data-ttu-id="68629-171">Członek</span><span class="sxs-lookup"><span data-stu-id="68629-171">Member</span></span> | <span data-ttu-id="68629-172">Platformy, które rzucają</span><span class="sxs-lookup"><span data-stu-id="68629-172">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="68629-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType>(tylko zestaw)</span><span class="sxs-lookup"><span data-stu-id="68629-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="68629-174">Linux</span><span class="sxs-lookup"><span data-stu-id="68629-174">Linux</span></span> |
| <span data-ttu-id="68629-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType>(tylko zestaw)</span><span class="sxs-lookup"><span data-stu-id="68629-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="68629-176">Linux</span><span class="sxs-lookup"><span data-stu-id="68629-176">Linux</span></span> |
| <xref:System.Diagnostics.Process.ProcessorAffinity?displayProperty=nameWithType> | <span data-ttu-id="68629-177">macOS</span><span class="sxs-lookup"><span data-stu-id="68629-177">macOS</span></span> |
| <xref:System.Diagnostics.Process.MainWindowHandle?displayProperty=nameWithType> | <span data-ttu-id="68629-178">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="68629-178">Linux and macOS</span></span> |
| <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> | <span data-ttu-id="68629-179">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="68629-179">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.UserName?displayProperty=nameWithType> | <span data-ttu-id="68629-180">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="68629-180">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.PasswordInClearText?displayProperty=nameWithType> | <span data-ttu-id="68629-181">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="68629-181">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.Domain?displayProperty=nameWithType> | <span data-ttu-id="68629-182">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="68629-182">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.LoadUserProfile?displayProperty=nameWithType> | <span data-ttu-id="68629-183">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="68629-183">Linux and macOS</span></span> |
| <span data-ttu-id="68629-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType>(tylko zestaw)</span><span class="sxs-lookup"><span data-stu-id="68629-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="68629-185">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="68629-185">Linux and macOS</span></span> |
| <span data-ttu-id="68629-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType>(tylko dostać)</span><span class="sxs-lookup"><span data-stu-id="68629-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="68629-187">macOS</span><span class="sxs-lookup"><span data-stu-id="68629-187">macOS</span></span> |
| <span data-ttu-id="68629-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType>(tylko zestaw)</span><span class="sxs-lookup"><span data-stu-id="68629-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="68629-189">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="68629-189">Linux and macOS</span></span> |

## <a name="systemio"></a><span data-ttu-id="68629-190">System.IO</span><span class="sxs-lookup"><span data-stu-id="68629-190">System.IO</span></span>

| <span data-ttu-id="68629-191">Członek</span><span class="sxs-lookup"><span data-stu-id="68629-191">Member</span></span> | <span data-ttu-id="68629-192">Platformy, które rzucają</span><span class="sxs-lookup"><span data-stu-id="68629-192">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.FileSystemInfo.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="68629-193">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-193">All</span></span> |
| <xref:System.IO.FileSystemInfo.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="68629-194">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-194">All</span></span> |

## <a name="systemiopipes"></a><span data-ttu-id="68629-195">System.IO.Rury</span><span class="sxs-lookup"><span data-stu-id="68629-195">System.IO.Pipes</span></span>

| <span data-ttu-id="68629-196">Członek</span><span class="sxs-lookup"><span data-stu-id="68629-196">Member</span></span> | <span data-ttu-id="68629-197">Platformy, które rzucają</span><span class="sxs-lookup"><span data-stu-id="68629-197">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.Pipes.NamedPipeClientStream.NumberOfServerInstances?displayProperty=nameWithType> | <span data-ttu-id="68629-198">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="68629-198">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName?displayProperty=nameWithType> | <span data-ttu-id="68629-199">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="68629-199">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.InBufferSize?displayProperty=nameWithType> | <span data-ttu-id="68629-200">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="68629-200">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.OutBufferSize?displayProperty=nameWithType> | <span data-ttu-id="68629-201">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="68629-201">Linux and macOS</span></span> |
| <span data-ttu-id="68629-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType>(tylko zestaw)</span><span class="sxs-lookup"><span data-stu-id="68629-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="68629-203">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="68629-203">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.WaitForPipeDrain?displayProperty=nameWithType> | <span data-ttu-id="68629-204">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="68629-204">Linux and macOS</span></span> |

## <a name="systemmedia"></a><span data-ttu-id="68629-205">System.Media</span><span class="sxs-lookup"><span data-stu-id="68629-205">System.Media</span></span>

| <span data-ttu-id="68629-206">Członek</span><span class="sxs-lookup"><span data-stu-id="68629-206">Member</span></span> | <span data-ttu-id="68629-207">Platformy, które rzucają</span><span class="sxs-lookup"><span data-stu-id="68629-207">Platforms that throw</span></span> |
| - | - |
| <xref:System.Media.SoundPlayer.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="68629-208">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-208">All</span></span> |

## <a name="systemnet"></a><span data-ttu-id="68629-209">System.Net</span><span class="sxs-lookup"><span data-stu-id="68629-209">System.Net</span></span>

| <span data-ttu-id="68629-210">Członek</span><span class="sxs-lookup"><span data-stu-id="68629-210">Member</span></span> | <span data-ttu-id="68629-211">Platformy, które rzucają</span><span class="sxs-lookup"><span data-stu-id="68629-211">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.AuthenticationManager.Authenticate(System.String,System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="68629-212">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-212">All</span></span> |
| <xref:System.Net.AuthenticationManager.PreAuthenticate(System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="68629-213">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-213">All</span></span> |
| <xref:System.Net.FileWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="68629-214">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-214">All</span></span> |
| <xref:System.Net.FileWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="68629-215">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-215">All</span></span> |
| <xref:System.Net.FileWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="68629-216">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-216">All</span></span> |
| <xref:System.Net.FileWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="68629-217">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-217">All</span></span> |
| <xref:System.Net.HttpWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="68629-218">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-218">All</span></span> |
| <xref:System.Net.HttpWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="68629-219">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-219">All</span></span> |
| <xref:System.Net.HttpWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="68629-220">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-220">All</span></span> |
| <xref:System.Net.HttpWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="68629-221">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-221">All</span></span> |
| <xref:System.Net.WebProxy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="68629-222">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-222">All</span></span> |
| <xref:System.Net.WebProxy.GetDefaultProxy?displayProperty=nameWithType> | <span data-ttu-id="68629-223">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-223">All</span></span> |
| <xref:System.Net.WebProxy.GetObjectData%2A?displayProperty=nameWithType> | <span data-ttu-id="68629-224">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-224">All</span></span> |
| <xref:System.Net.WebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="68629-225">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-225">All</span></span> |
| <xref:System.Net.WebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="68629-226">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-226">All</span></span> |
| <xref:System.Net.WebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="68629-227">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-227">All</span></span> |
| <xref:System.Net.WebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="68629-228">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-228">All</span></span> |

## <a name="systemnetnetworkinformation"></a><span data-ttu-id="68629-229">Informacje systemowe.net.networkInformacja</span><span class="sxs-lookup"><span data-stu-id="68629-229">System.Net.NetworkInformation</span></span>

| <span data-ttu-id="68629-230">Członek</span><span class="sxs-lookup"><span data-stu-id="68629-230">Member</span></span> | <span data-ttu-id="68629-231">Platformy, które rzucają</span><span class="sxs-lookup"><span data-stu-id="68629-231">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.NetworkInformation.Ping.Send%2A?displayProperty=nameWithType> | <span data-ttu-id="68629-232">Windows (UWP)</span><span class="sxs-lookup"><span data-stu-id="68629-232">Windows (UWP)</span></span> |

## <a name="systemnetsockets"></a><span data-ttu-id="68629-233">System.net.sockets</span><span class="sxs-lookup"><span data-stu-id="68629-233">System.Net.Sockets</span></span>

| <span data-ttu-id="68629-234">Członek</span><span class="sxs-lookup"><span data-stu-id="68629-234">Member</span></span> | <span data-ttu-id="68629-235">Platformy, które rzucają</span><span class="sxs-lookup"><span data-stu-id="68629-235">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.Sockets.Socket.%23ctor(System.Net.Sockets.SocketInformation)> | <span data-ttu-id="68629-236">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-236">All</span></span> |
| <xref:System.Net.Sockets.Socket.DuplicateAndClose(System.Int32)?displayProperty=nameWithType> | <span data-ttu-id="68629-237">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-237">All</span></span> |

## <a name="systemnetwebsockets"></a><span data-ttu-id="68629-238">Zestawy systemowe system.net.websockets</span><span class="sxs-lookup"><span data-stu-id="68629-238">System.Net.WebSockets</span></span>

| <span data-ttu-id="68629-239">Członek</span><span class="sxs-lookup"><span data-stu-id="68629-239">Member</span></span> | <span data-ttu-id="68629-240">Platformy, które rzucają</span><span class="sxs-lookup"><span data-stu-id="68629-240">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.WebSockets.WebSocket.RegisterPrefixes?displayProperty=nameWithType> | <span data-ttu-id="68629-241">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-241">All</span></span> |

## <a name="systemreflection"></a><span data-ttu-id="68629-242">System.reflection</span><span class="sxs-lookup"><span data-stu-id="68629-242">System.Reflection</span></span>

| <span data-ttu-id="68629-243">Członek</span><span class="sxs-lookup"><span data-stu-id="68629-243">Member</span></span> | <span data-ttu-id="68629-244">Platformy, które rzucają</span><span class="sxs-lookup"><span data-stu-id="68629-244">Platforms that throw</span></span> |
| - | - |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> | <span data-ttu-id="68629-245">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-245">All</span></span> |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom(System.String)?displayProperty=nameWithType> | <span data-ttu-id="68629-246">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-246">All</span></span> |
| <xref:System.Reflection.AssemblyName.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="68629-247">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-247">All</span></span> |
| <xref:System.Reflection.AssemblyName.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="68629-248">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-248">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.String)> | <span data-ttu-id="68629-249">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-249">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="68629-250">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-250">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.PublicKey?displayProperty=nameWithType> | <span data-ttu-id="68629-251">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-251">All</span></span> |

## <a name="systemruntimecompilerservices"></a><span data-ttu-id="68629-252">System.runtime.compilerservices</span><span class="sxs-lookup"><span data-stu-id="68629-252">System.Runtime.CompilerServices</span></span>

| <span data-ttu-id="68629-253">Członek</span><span class="sxs-lookup"><span data-stu-id="68629-253">Member</span></span> | <span data-ttu-id="68629-254">Platformy, które rzucają</span><span class="sxs-lookup"><span data-stu-id="68629-254">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType> | <span data-ttu-id="68629-255">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-255">All</span></span> |

## <a name="systemruntimeinteropservices"></a><span data-ttu-id="68629-256">System.runtime.interopservices</span><span class="sxs-lookup"><span data-stu-id="68629-256">System.Runtime.InteropServices</span></span>

| <span data-ttu-id="68629-257">Członek</span><span class="sxs-lookup"><span data-stu-id="68629-257">Member</span></span> | <span data-ttu-id="68629-258">Platformy, które rzucają</span><span class="sxs-lookup"><span data-stu-id="68629-258">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.InteropServices.Marshal.GetIDispatchForObject(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="68629-259">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-259">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.SystemConfigurationFile?displayProperty=nameWithType> | <span data-ttu-id="68629-260">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-260">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsIntPtr(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="68629-261">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-261">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsObject(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="68629-262">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-262">All</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.StringToHString(System.String)?displayProperty=nameWithType> | <span data-ttu-id="68629-263">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="68629-263">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.PtrToStringHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="68629-264">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="68629-264">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.FreeHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="68629-265">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="68629-265">Linux and macOS</span></span> |

## <a name="systemruntimeserialization"></a><span data-ttu-id="68629-266">System.Runtime.Serialization</span><span class="sxs-lookup"><span data-stu-id="68629-266">System.Runtime.Serialization</span></span>

| <span data-ttu-id="68629-267">Członek</span><span class="sxs-lookup"><span data-stu-id="68629-267">Member</span></span> | <span data-ttu-id="68629-268">Platformy, które rzucają</span><span class="sxs-lookup"><span data-stu-id="68629-268">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas?displayProperty=nameWithType> | <span data-ttu-id="68629-269">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-269">All</span></span> |

## <a name="systemsecurity"></a><span data-ttu-id="68629-270">System.Bezpieczeństwo</span><span class="sxs-lookup"><span data-stu-id="68629-270">System.Security</span></span>

| <span data-ttu-id="68629-271">Członek</span><span class="sxs-lookup"><span data-stu-id="68629-271">Member</span></span> | <span data-ttu-id="68629-272">Platformy, które rzucają</span><span class="sxs-lookup"><span data-stu-id="68629-272">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.CodeAccessPermission.Deny?displayProperty=nameWithType> | <span data-ttu-id="68629-273">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-273">All</span></span> |
| <xref:System.Security.CodeAccessPermission.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="68629-274">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-274">All</span></span> |
| <xref:System.Security.PermissionSet.ConvertPermissionSet(System.String,System.Byte[],System.String)?displayProperty=nameWithType> | <span data-ttu-id="68629-275">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-275">All</span></span> |
| <xref:System.Security.PermissionSet.Deny?displayProperty=nameWithType> | <span data-ttu-id="68629-276">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-276">All</span></span> |
| <xref:System.Security.PermissionSet.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="68629-277">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-277">All</span></span> |
| <xref:System.Security.SecurityContext.Capture?displayProperty=nameWithType> | <span data-ttu-id="68629-278">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-278">All</span></span> |
| <xref:System.Security.SecurityContext.CreateCopy?displayProperty=nameWithType> | <span data-ttu-id="68629-279">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-279">All</span></span> |
| <xref:System.Security.SecurityContext.Dispose?displayProperty=nameWithType> | <span data-ttu-id="68629-280">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-280">All</span></span> |
| <xref:System.Security.SecurityContext.IsFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="68629-281">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-281">All</span></span> |
| <xref:System.Security.SecurityContext.IsWindowsIdentityFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="68629-282">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-282">All</span></span> |
| <xref:System.Security.SecurityContext.RestoreFlow?displayProperty=nameWithType> | <span data-ttu-id="68629-283">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-283">All</span></span> |
| <xref:System.Security.SecurityContext.Run(System.Security.SecurityContext,System.Threading.ContextCallback,System.Object)?displayProperty=nameWithType> | <span data-ttu-id="68629-284">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-284">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlow?displayProperty=nameWithType> | <span data-ttu-id="68629-285">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-285">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity?displayProperty=nameWithType> | <span data-ttu-id="68629-286">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-286">All</span></span> |

## <a name="systemsecurityclaims"></a><span data-ttu-id="68629-287">System.security.claims</span><span class="sxs-lookup"><span data-stu-id="68629-287">System.Security.Claims</span></span>

| <span data-ttu-id="68629-288">Członek</span><span class="sxs-lookup"><span data-stu-id="68629-288">Member</span></span> | <span data-ttu-id="68629-289">Platformy, które rzucają</span><span class="sxs-lookup"><span data-stu-id="68629-289">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Claims.ClaimsPrincipal.%23ctor> | <span data-ttu-id="68629-290">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-290">All</span></span> |
| <xref:System.Security.Claims.ClaimsPrincipal.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="68629-291">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-291">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo)> | <span data-ttu-id="68629-292">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-292">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="68629-293">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-293">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="68629-294">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-294">All</span></span> |

## <a name="systemsecuritycryptography"></a><span data-ttu-id="68629-295">System.security.cryptography</span><span class="sxs-lookup"><span data-stu-id="68629-295">System.Security.Cryptography</span></span>

| <span data-ttu-id="68629-296">Członek</span><span class="sxs-lookup"><span data-stu-id="68629-296">Member</span></span> | <span data-ttu-id="68629-297">Platformy, które rzucają</span><span class="sxs-lookup"><span data-stu-id="68629-297">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="68629-298">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-298">All</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.%23ctor%2A> | <span data-ttu-id="68629-299">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="68629-299">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Accessible?displayProperty=nameWithType> | <span data-ttu-id="68629-300">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="68629-300">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Exportable?displayProperty=nameWithType> | <span data-ttu-id="68629-301">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="68629-301">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.HardwareDevice?displayProperty=nameWithType> | <span data-ttu-id="68629-302">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="68629-302">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="68629-303">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="68629-303">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyNumber?displayProperty=nameWithType> | <span data-ttu-id="68629-304">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="68629-304">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.MachineKeyStore?displayProperty=nameWithType> | <span data-ttu-id="68629-305">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="68629-305">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Protected?displayProperty=nameWithType> | <span data-ttu-id="68629-306">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="68629-306">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderName?displayProperty=nameWithType> | <span data-ttu-id="68629-307">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="68629-307">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderType?displayProperty=nameWithType> | <span data-ttu-id="68629-308">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="68629-308">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.RandomlyGenerated?displayProperty=nameWithType> | <span data-ttu-id="68629-309">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="68629-309">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Removable?displayProperty=nameWithType> | <span data-ttu-id="68629-310">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="68629-310">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.UniqueKeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="68629-311">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="68629-311">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="68629-312">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-312">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | <span data-ttu-id="68629-313">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-313">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="68629-314">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-314">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashCore%2A?displayProperty=nameWithType> | <span data-ttu-id="68629-315">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-315">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashFinal%2A?displayProperty=nameWithType> | <span data-ttu-id="68629-316">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-316">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Initialize%2A?displayProperty=nameWithType> | <span data-ttu-id="68629-317">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-317">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="68629-318">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-318">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="68629-319">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-319">All</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Protect%2A?displayProperty=nameWithType> | <span data-ttu-id="68629-320">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="68629-320">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A?displayProperty=nameWithType> | <span data-ttu-id="68629-321">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="68629-321">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.RSA.FromXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="68629-322">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-322">All</span></span> |
| <xref:System.Security.Cryptography.RSA.ToXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="68629-323">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-323">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="68629-324">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-324">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="68629-325">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-325">All</span></span> |

## <a name="systemsecuritycryptographypkcs"></a><span data-ttu-id="68629-326">System.Security.Cryptography.Pkcs</span><span class="sxs-lookup"><span data-stu-id="68629-326">System.Security.Cryptography.Pkcs</span></span>

| <span data-ttu-id="68629-327">Członek</span><span class="sxs-lookup"><span data-stu-id="68629-327">Member</span></span> | <span data-ttu-id="68629-328">Platformy, które rzucają</span><span class="sxs-lookup"><span data-stu-id="68629-328">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.Pkcs.CmsSigner.%23ctor(System.Security.Cryptography.CspParameters)> | <span data-ttu-id="68629-329">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-329">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="68629-330">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-330">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignerInfo.ComputeCounterSignature?displayProperty=nameWithType> | <span data-ttu-id="68629-331">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-331">All</span></span> |

## <a name="systemsecuritycryptographyx509certificates"></a><span data-ttu-id="68629-332">Certyfikaty systemowe.Security.Cryptography.X509Certificates</span><span class="sxs-lookup"><span data-stu-id="68629-332">System.Security.Cryptography.X509Certificates</span></span>

| <span data-ttu-id="68629-333">Członek</span><span class="sxs-lookup"><span data-stu-id="68629-333">Member</span></span> | <span data-ttu-id="68629-334">Platformy, które rzucają</span><span class="sxs-lookup"><span data-stu-id="68629-334">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="68629-335">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-335">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Import%2A?displayProperty=nameWithType> | <span data-ttu-id="68629-336">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-336">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="68629-337">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-337">All</span></span> |
| <span data-ttu-id="68629-338"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType>(tylko zestaw)</span><span class="sxs-lookup"><span data-stu-id="68629-338"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="68629-339">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-339">All</span></span> |

## <a name="systemsecurityauthenticationextendedprotection"></a><span data-ttu-id="68629-340">System.Security.Authentication.ExtendedProtection</span><span class="sxs-lookup"><span data-stu-id="68629-340">System.Security.Authentication.ExtendedProtection</span></span>

| <span data-ttu-id="68629-341">Członek</span><span class="sxs-lookup"><span data-stu-id="68629-341">Member</span></span> | <span data-ttu-id="68629-342">Platformy, które rzucają</span><span class="sxs-lookup"><span data-stu-id="68629-342">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="68629-343">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-343">All</span></span> |

## <a name="systemsecuritypolicy"></a><span data-ttu-id="68629-344">System.Security.Policy</span><span class="sxs-lookup"><span data-stu-id="68629-344">System.Security.Policy</span></span>

| <span data-ttu-id="68629-345">Członek</span><span class="sxs-lookup"><span data-stu-id="68629-345">Member</span></span> | <span data-ttu-id="68629-346">Platformy, które rzucają</span><span class="sxs-lookup"><span data-stu-id="68629-346">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Policy.Hash.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="68629-347">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-347">All</span></span> |

## <a name="systemserviceprocessservicecontroller"></a><span data-ttu-id="68629-348">System.ServiceProcess.ServiceKontroler</span><span class="sxs-lookup"><span data-stu-id="68629-348">System.ServiceProcess.ServiceController</span></span>

| <span data-ttu-id="68629-349">Członek</span><span class="sxs-lookup"><span data-stu-id="68629-349">Member</span></span> | <span data-ttu-id="68629-350">Platformy, które rzucają</span><span class="sxs-lookup"><span data-stu-id="68629-350">Platforms that throw</span></span> |
| - | - |
| <xref:System.ServiceProcess.TimeoutException.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="68629-351">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-351">All</span></span> |

## <a name="systemtextregularexpressions"></a><span data-ttu-id="68629-352">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="68629-352">System.Text.RegularExpressions</span></span>

| <span data-ttu-id="68629-353">Członek</span><span class="sxs-lookup"><span data-stu-id="68629-353">Member</span></span> | <span data-ttu-id="68629-354">Platformy, które rzucają</span><span class="sxs-lookup"><span data-stu-id="68629-354">Platforms that throw</span></span> |
| - | - |
| <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> | <span data-ttu-id="68629-355">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-355">All</span></span> |

## <a name="systemthreading"></a><span data-ttu-id="68629-356">System.threading</span><span class="sxs-lookup"><span data-stu-id="68629-356">System.Threading</span></span>

| <span data-ttu-id="68629-357">Członek</span><span class="sxs-lookup"><span data-stu-id="68629-357">Member</span></span> | <span data-ttu-id="68629-358">Platformy, które rzucają</span><span class="sxs-lookup"><span data-stu-id="68629-358">Platforms that throw</span></span> |
| - | - |
| <xref:System.Threading.CompressedStack.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="68629-359">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-359">All</span></span> |
| <xref:System.Threading.ExecutionContext.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="68629-360">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-360">All</span></span> |
| <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> | <span data-ttu-id="68629-361">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-361">All</span></span> |
| <xref:System.Threading.Thread.ResetAbort?displayProperty=nameWithType> | <span data-ttu-id="68629-362">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-362">All</span></span> |
| <xref:System.Threading.Thread.Resume?displayProperty=nameWithType> | <span data-ttu-id="68629-363">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-363">All</span></span> |
| <xref:System.Threading.Thread.Suspend?displayProperty=nameWithType> | <span data-ttu-id="68629-364">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-364">All</span></span> |

## <a name="systemxml"></a><span data-ttu-id="68629-365">System.Xml</span><span class="sxs-lookup"><span data-stu-id="68629-365">System.Xml</span></span>

| <span data-ttu-id="68629-366">Członek</span><span class="sxs-lookup"><span data-stu-id="68629-366">Member</span></span> | <span data-ttu-id="68629-367">Platformy, które rzucają</span><span class="sxs-lookup"><span data-stu-id="68629-367">Platforms that throw</span></span> |
| - | - |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.Byte[],System.Int32,System.Int32,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="68629-368">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-368">All</span></span> |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.IO.Stream,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="68629-369">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-369">All</span></span> |
| <xref:System.Xml.XmlDictionaryWriter.CreateMtomWriter(System.IO.Stream,System.Text.Encoding,System.Int32,System.String,System.String,System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="68629-370">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="68629-370">All</span></span> |

## <a name="see-also"></a><span data-ttu-id="68629-371">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="68629-371">See also</span></span>

- [<span data-ttu-id="68629-372">Przerywanie zmian migracji z programu .NET Framework do programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="68629-372">Breaking changes for migration from .NET Framework to .NET Core</span></span>](../compatibility/fx-core.md)
- [<span data-ttu-id="68629-373">Serializacja binarna w rdzeniu .NET</span><span class="sxs-lookup"><span data-stu-id="68629-373">Binary serialization in .NET Core</span></span>](../../standard/serialization/binary-serialization.md#net-core)
- [<span data-ttu-id="68629-374">Analizator przenośności .NET</span><span class="sxs-lookup"><span data-stu-id="68629-374">.NET portability analyzer</span></span>](../../standard/analyzers/portability-analyzer.md)
