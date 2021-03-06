INCLUDE_DIRECTORIES( ${CMAKE_CURRENT_SOURCE_DIR} )

# public API headers go in the src/EnergyPlus/public folder
INCLUDE_DIRECTORIES( ${CMAKE_CURRENT_SOURCE_DIR}/public )

# Don't reconfigure this file when moving from PROFILE_GENERATE to PROFILE_USE
if(NOT PROFILE_USE)
  configure_file( DataStringGlobals.in.cc "${CMAKE_CURRENT_BINARY_DIR}/DataStringGlobals.cc" )
  configure_file( ConfiguredFunctions.in.cc "${CMAKE_CURRENT_BINARY_DIR}/ConfiguredFunctions.cc" )
  file( WRITE "${CMAKE_CURRENT_BINARY_DIR}/EmbeddedEpJSONSchema.cc" "Will be filled in later by GenerateEmbeddedEpJSONSchema" )
endif()

SET( SRC
  "${CMAKE_SOURCE_DIR}/third_party/milo/dtoa.h"
  "${CMAKE_SOURCE_DIR}/third_party/milo/itoa.h"
  "${CMAKE_SOURCE_DIR}/third_party/milo/diyfp.h"
  "${CMAKE_SOURCE_DIR}/third_party/milo/ieee754.h"
  AirflowNetworkBalanceManager.cc
  AirflowNetworkBalanceManager.hh
  AirflowNetworkSolver.cc
  AirflowNetworkSolver.hh
  AirTerminalUnit.hh
  BaseboardElectric.cc
  BaseboardElectric.hh
  BaseboardRadiator.cc
  BaseboardRadiator.hh
  BoilerSteam.cc
  BoilerSteam.hh
  Boilers.cc
  Boilers.hh
  BranchInputManager.cc
  BranchInputManager.hh
  BranchNodeConnections.cc
  BranchNodeConnections.hh
  CTElectricGenerator.cc
  CTElectricGenerator.hh
  ChilledCeilingPanelSimple.cc
  ChilledCeilingPanelSimple.hh
  ChillerAbsorption.cc
  ChillerAbsorption.hh
  ChillerElectricEIR.cc
  ChillerElectricEIR.hh
  ChillerExhaustAbsorption.cc
  ChillerExhaustAbsorption.hh
  ChillerGasAbsorption.cc
  ChillerGasAbsorption.hh
  ChillerIndirectAbsorption.cc
  ChillerIndirectAbsorption.hh
  ChillerReformulatedEIR.cc
  ChillerReformulatedEIR.hh
  CondenserLoopTowers.cc
  CondenserLoopTowers.hh
  ConductionTransferFunctionCalc.cc
  ConductionTransferFunctionCalc.hh
  ConfiguredFunctions.hh
  "${CMAKE_CURRENT_BINARY_DIR}/ConfiguredFunctions.cc"
  ConvectionCoefficients.cc
  ConvectionCoefficients.hh
  CoolTower.cc
  CoolTower.hh
  CostEstimateManager.cc
  CostEstimateManager.hh
  CrossVentMgr.cc
  CrossVentMgr.hh
  CurveManager.cc
  CurveManager.hh
  DElightManagerF.cc
  DElightManagerF.hh
  DXCoils.cc
  DXCoils.hh
  DXFEarClipping.cc
  DXFEarClipping.hh
  DataAirLoop.cc
  DataAirLoop.hh
  DataAirSystems.cc
  DataAirSystems.hh
  DataAirflowNetwork.cc
  DataAirflowNetwork.hh
  DataBSDFWindow.cc
  DataBSDFWindow.hh
  DataBranchAirLoopPlant.cc
  DataBranchAirLoopPlant.hh
  DataBranchNodeConnections.cc
  DataBranchNodeConnections.hh
  DataComplexFenestration.cc
  DataComplexFenestration.hh
  DataContaminantBalance.cc
  DataContaminantBalance.hh
  DataConvergParams.cc
  DataConvergParams.hh
  DataConversions.cc
  DataConversions.hh
  DataCostEstimate.cc
  DataCostEstimate.hh
  DataDElight.cc
  DataDElight.hh
  DataDaylighting.cc
  DataDaylighting.hh
  DataDaylightingDevices.cc
  DataDaylightingDevices.hh
  DataDefineEquip.cc
  DataDefineEquip.hh
  DataEnvironment.cc
  DataEnvironment.hh
  DataErrorTracking.cc
  DataErrorTracking.hh
  DataGenerators.cc
  DataGenerators.hh
  DataGlobalConstants.cc
  DataGlobalConstants.hh
  DataGlobals.cc
  DataGlobals.hh
  DataHVACControllers.cc
  DataHVACControllers.hh
  DataHVACGlobals.cc
  DataHVACGlobals.hh
  DataHeatBalFanSys.cc
  DataHeatBalFanSys.hh
  DataHeatBalSurface.cc
  DataHeatBalSurface.hh
  DataHeatBalance.cc
  DataHeatBalance.hh
  DataIPShortCuts.cc
  DataIPShortCuts.hh
  DataLoopNode.cc
  DataLoopNode.hh
  DataMoistureBalance.cc
  DataMoistureBalance.hh
  DataMoistureBalanceEMPD.cc
  DataMoistureBalanceEMPD.hh
  DataOutputs.cc
  DataOutputs.hh
  DataPhotovoltaics.cc
  DataPhotovoltaics.hh
  DataPlant.cc
  DataPlant.hh
  DataPrecisionGlobals.cc
  DataPrecisionGlobals.hh
  DataReportingFlags.cc
  DataReportingFlags.hh
  DataRoomAirModel.cc
  DataRoomAirModel.hh
  DataRootFinder.cc
  DataRootFinder.hh
  DataRuntimeLanguage.cc
  DataRuntimeLanguage.hh
  DataShadowingCombinations.cc
  DataShadowingCombinations.hh
  DataSizing.cc
  DataSizing.hh
  "${CMAKE_CURRENT_BINARY_DIR}/DataStringGlobals.cc"
  DataStringGlobals.hh
  DataSurfaceColors.cc
  DataSurfaceColors.hh
  DataSurfaceLists.cc
  DataSurfaceLists.hh
  DataSurfaces.cc
  DataSurfaces.hh
  DataSystemVariables.cc
  DataSystemVariables.hh
  DataTimings.cc
  DataTimings.hh
  DataUCSDSharedData.cc
  DataUCSDSharedData.hh
  DataVectorTypes.hh
  DataViewFactorInformation.cc
  DataViewFactorInformation.hh
  DataWater.cc
  DataWater.hh
  DataWindowEquivalentLayer.cc
  DataWindowEquivalentLayer.hh
  DataZoneControls.cc
  DataZoneControls.hh
  DataZoneEnergyDemands.cc
  DataZoneEnergyDemands.hh
  DataZoneEquipment.cc
  DataZoneEquipment.hh
  DaylightingDevices.cc
  DaylightingDevices.hh
  DaylightingManager.cc
  DaylightingManager.hh
  DemandManager.cc
  DemandManager.hh
  DesiccantDehumidifiers.cc
  DesiccantDehumidifiers.hh
  DirectAirManager.cc
  DirectAirManager.hh
  DisplacementVentMgr.cc
  DisplacementVentMgr.hh
  DisplayRoutines.cc
  DisplayRoutines.hh
  DualDuct.cc
  DualDuct.hh
  EMSManager.cc
  EMSManager.hh
  EarthTube.cc
  EarthTube.hh
  EcoRoofManager.cc
  EcoRoofManager.hh
  EconomicLifeCycleCost.cc
  EconomicLifeCycleCost.hh
  EconomicTariff.cc
  EconomicTariff.hh
  ElectricBaseboardRadiator.cc
  ElectricBaseboardRadiator.hh
  ElectricPowerServiceManager.hh
  ElectricPowerServiceManager.cc
  EnergyPlus.hh
  EvaporativeCoolers.cc
  EvaporativeCoolers.hh
  EvaporativeFluidCoolers.cc
  EvaporativeFluidCoolers.hh
  ExteriorEnergyUse.cc
  ExteriorEnergyUse.hh
  ExternalInterface.cc
  ExternalInterface.hh
  FanCoilUnits.cc
  FanCoilUnits.hh
  Fans.cc
  Fans.hh
  FaultsManager.cc
  FaultsManager.hh
  FileSystem.cc
  FileSystem.hh
  FluidCoolers.cc
  FluidCoolers.hh
  FluidProperties.cc
  FluidProperties.hh
  FuelCellElectricGenerator.cc
  FuelCellElectricGenerator.hh
  Furnaces.cc
  Furnaces.hh
  General.cc
  General.hh
  GeneralRoutines.cc
  GeneralRoutines.hh
  GeneratorDynamicsManager.cc
  GeneratorDynamicsManager.hh
  GeneratorFuelSupply.cc
  GeneratorFuelSupply.hh
  GlobalNames.cc
  GlobalNames.hh
  GroundHeatExchangers.cc
  GroundHeatExchangers.hh
  GroundTemperatureModeling/BaseGroundTemperatureModel.hh
  GroundTemperatureModeling/FiniteDifferenceGroundTemperatureModel.cc
  GroundTemperatureModeling/FiniteDifferenceGroundTemperatureModel.hh
  GroundTemperatureModeling/GroundTemperatureModelManager.cc
  GroundTemperatureModeling/GroundTemperatureModelManager.hh
  HVACControllers.cc
  HVACControllers.hh
  HVACCooledBeam.cc
  HVACCooledBeam.hh
  HVACDXHeatPumpSystem.cc
  HVACDXHeatPumpSystem.hh
  HVACDXSystem.cc
  HVACDXSystem.hh
  HVACDuct.cc
  HVACDuct.hh
  HVACFan.cc
  HVACFan.hh
  HVACFourPipeBeam.cc
  HVACFourPipeBeam.hh
  HVACHXAssistedCoolingCoil.cc
  HVACHXAssistedCoolingCoil.hh
  HVACInterfaceManager.cc
  HVACInterfaceManager.hh
  HVACManager.cc
  HVACManager.hh
  HVACMultiSpeedHeatPump.cc
  HVACMultiSpeedHeatPump.hh
  HVACSingleDuctInduc.cc
  HVACSingleDuctInduc.hh
  HVACSizingSimulationManager.cc
  HVACSizingSimulationManager.hh
  HVACStandAloneERV.cc
  HVACStandAloneERV.hh
  HVACUnitaryBypassVAV.cc
  HVACUnitaryBypassVAV.hh
  HVACUnitarySystem.cc
  HVACUnitarySystem.hh
  HVACVariableRefrigerantFlow.cc
  HVACVariableRefrigerantFlow.hh
  HWBaseboardRadiator.cc
  HWBaseboardRadiator.hh
  HeatBalFiniteDiffManager.cc
  HeatBalFiniteDiffManager.hh
  HeatBalanceKivaManager.cc
  HeatBalanceKivaManager.hh
  HeatBalanceAirManager.cc
  HeatBalanceAirManager.hh
  HeatBalanceHAMTManager.cc
  HeatBalanceHAMTManager.hh
  HeatBalanceIntRadExchange.cc
  HeatBalanceIntRadExchange.hh
  HeatBalanceInternalHeatGains.cc
  HeatBalanceInternalHeatGains.hh
  HeatBalanceManager.cc
  HeatBalanceManager.hh
  HeatBalanceMovableInsulation.cc
  HeatBalanceMovableInsulation.hh
  HeatBalanceSurfaceManager.cc
  HeatBalanceSurfaceManager.hh
  HeatPumpWaterToWaterCOOLING.cc
  HeatPumpWaterToWaterCOOLING.hh
  HeatPumpWaterToWaterHEATING.cc
  HeatPumpWaterToWaterHEATING.hh
  HeatPumpWaterToWaterSimple.cc
  HeatPumpWaterToWaterSimple.hh
  HeatRecovery.cc
  HeatRecovery.hh
  HeatingCoils.cc
  HeatingCoils.hh
  HighTempRadiantSystem.cc
  HighTempRadiantSystem.hh
  Humidifiers.cc
  Humidifiers.hh
  HybridUnitaryAirConditioners.cc
  HybridUnitaryAirConditioners.hh
  HybridEvapCoolingModel.cc
  HybridEvapCoolingModel.hh
  HybridModel.cc
  HybridModel.hh
  GroundTemperatureModeling/KusudaAchenbachGroundTemperatureModel.cc
  GroundTemperatureModeling/KusudaAchenbachGroundTemperatureModel.hh
  GroundTemperatureModeling/SiteBuildingSurfaceGroundTemperatures.cc
  GroundTemperatureModeling/SiteBuildingSurfaceGroundTemperatures.hh
  GroundTemperatureModeling/SiteDeepGroundTemperatures.cc
  GroundTemperatureModeling/SiteDeepGroundTemperatures.hh
  GroundTemperatureModeling/SiteFCFactorMethodGroundTemperatures.cc
  GroundTemperatureModeling/SiteFCFactorMethodGroundTemperatures.hh
  GroundTemperatureModeling/SiteShallowGroundTemperatures.cc
  GroundTemperatureModeling/SiteShallowGroundTemperatures.hh
  GroundTemperatureModeling/XingGroundTemperatureModel.cc
  GroundTemperatureModeling/XingGroundTemperatureModel.hh
  ICEngineElectricGenerator.cc
  ICEngineElectricGenerator.hh
  IceThermalStorage.cc
  IceThermalStorage.hh
  InputProcessing/DataStorage.hh
  InputProcessing/EmbeddedEpJSONSchema.hh
  "${CMAKE_CURRENT_BINARY_DIR}/EmbeddedEpJSONSchema.cc"
  InputProcessing/IdfParser.cc
  InputProcessing/IdfParser.hh
  InputProcessing/InputProcessor.cc
  InputProcessing/InputProcessor.hh
  InputProcessing/InputValidation.cc
  InputProcessing/InputValidation.hh
  IntegratedHeatPump.cc
  IntegratedHeatPump.hh
  InternalHeatGains.cc
  InternalHeatGains.hh
  LowTempRadiantSystem.cc
  LowTempRadiantSystem.hh
  MatrixDataManager.cc
  MatrixDataManager.hh
  MicroCHPElectricGenerator.cc
  MicroCHPElectricGenerator.hh
  MicroturbineElectricGenerator.cc
  MicroturbineElectricGenerator.hh
  MixedAir.cc
  MixedAir.hh
  MixerComponent.cc
  MixerComponent.hh
  MoistureBalanceEMPDManager.cc
  MoistureBalanceEMPDManager.hh
  MundtSimMgr.cc
  MundtSimMgr.hh
  NodeInputManager.cc
  NodeInputManager.hh
  NonZoneEquipmentManager.cc
  NonZoneEquipmentManager.hh
  OutAirNodeManager.cc
  OutAirNodeManager.hh
  OutdoorAirUnit.cc
  OutdoorAirUnit.hh
  OutputProcessor.cc
  OutputProcessor.hh
  OutputReportPredefined.cc
  OutputReportPredefined.hh
  OutputReportTabular.cc
  OutputReportTabular.hh
  OutputReportTabularAnnual.cc
  OutputReportTabularAnnual.hh
  OutputReports.cc
  OutputReports.hh
  OutputReportData.cc
  OutputReportData.hh
  OutsideEnergySources.cc
  OutsideEnergySources.hh
  PackagedTerminalHeatPump.cc
  PackagedTerminalHeatPump.hh
  PackagedThermalStorageCoil.cc
  PackagedThermalStorageCoil.hh
  PhaseChangeModeling/HysteresisModel.cc
  PhaseChangeModeling/HysteresisModel.hh
  PhotovoltaicThermalCollectors.cc
  PhotovoltaicThermalCollectors.hh
  Photovoltaics.cc
  Photovoltaics.hh
  PierceSurface.hh
  PipeHeatTransfer.cc
  PipeHeatTransfer.hh
  Pipes.cc
  Pipes.hh
  Plant/CallingOrder.hh
  Plant/Enums.hh
  Plant/EquipAndOperations.hh
  Plant/LoopSidePumpInformation.hh
  Plant/PlantAvailManager.hh
  Plant/PlantConvergencePoint.hh
  Plant/LoopSideReportVars.hh
  Plant/MeterData.hh
  Plant/ReportBranchData.hh
  Plant/ReportCompData.hh
  Plant/ReportLoopData.hh
  Plant/ReportVars.hh
  Plant/Branch.hh
  Plant/Component.hh
  Plant/ConnectedLoopData.hh
  Plant/Connection.hh
  Plant/Loop.hh
  Plant/LoopSide.hh
  Plant/MixerData.hh
  Plant/SplitterData.hh
  Plant/Subcomponents.hh
  PlantCentralGSHP.cc
  PlantCentralGSHP.hh
  PlantChillers.cc
  PlantChillers.hh
  PlantComponent.hh
  PlantComponentTemperatureSources.cc
  PlantComponentTemperatureSources.hh
  PlantCondLoopOperation.cc
  PlantCondLoopOperation.hh
  PlantHeatExchangerFluidToFluid.cc
  PlantHeatExchangerFluidToFluid.hh
  PlantLoadProfile.cc
  PlantLoadProfile.hh
  Plant/PlantLocation.hh
  PlantLoopEquip.cc
  PlantLoopEquip.hh
  Plant/PlantLoopSolver.cc
  Plant/PlantLoopSolver.hh
  Plant/PlantManager.cc
  Plant/PlantManager.hh
  PlantPipingSystemsManager.cc
  PlantPipingSystemsManager.hh
  PlantPressureSystem.cc
  PlantPressureSystem.hh
  PlantUtilities.cc
  PlantUtilities.hh
  PlantValves.cc
  PlantValves.hh
  Platform.hh
  PollutionModule.cc
  PollutionModule.hh
  PondGroundHeatExchanger.cc
  PondGroundHeatExchanger.hh
  PoweredInductionUnits.cc
  PoweredInductionUnits.hh
  Psychrometrics.cc
  Psychrometrics.hh
  Pumps.cc
  Pumps.hh
  PurchasedAirManager.cc
  PurchasedAirManager.hh
  PVWatts.cc
  PVWatts.hh
  PVWattsSSC.cc
  PVWattsSSC.hh
  RefrigeratedCase.cc
  RefrigeratedCase.hh
  ReportCoilSelection.cc
  ReportCoilSelection.hh
  ReportSizingManager.cc
  ReportSizingManager.hh
  ReturnAirPathManager.cc
  ReturnAirPathManager.hh
  RoomAirModelAirflowNetwork.cc
  RoomAirModelAirflowNetwork.hh
  RoomAirModelManager.cc
  RoomAirModelManager.hh
  RoomAirModelUserTempPattern.cc
  RoomAirModelUserTempPattern.hh
  RootFinder.cc
  RootFinder.hh
  RuntimeLanguageProcessor.cc
  RuntimeLanguageProcessor.hh
  SQLiteProcedures.cc
  SQLiteProcedures.hh
  ScheduleManager.cc
  ScheduleManager.hh
  SetPointManager.cc
  SetPointManager.hh
  Shape.hh
  SimAirServingZones.cc
  SimAirServingZones.hh
  SimulationManager.cc
  SimulationManager.hh
  SingleDuct.cc
  SingleDuct.hh
  SizingAnalysisObjects.cc
  SizingAnalysisObjects.hh
  SizingManager.cc
  SizingManager.hh
  SolarCollectors.cc
  SolarCollectors.hh
  SolarReflectionManager.cc
  SolarReflectionManager.hh
  SolarShading.cc
  SolarShading.hh
  SortAndStringUtilities.cc
  SortAndStringUtilities.hh
  SplitterComponent.cc
  SplitterComponent.hh
  StandardRatings.cc
  StandardRatings.hh
  SteamBaseboardRadiator.cc
  SteamBaseboardRadiator.hh
  SteamCoils.cc
  SteamCoils.hh
  SurfaceGeometry.cc
  SurfaceGeometry.hh
  SurfaceGroundHeatExchanger.cc
  SurfaceGroundHeatExchanger.hh
  SurfaceOctree.cc
  SurfaceOctree.hh
  SwimmingPool.cc
  SwimmingPool.hh
  SystemAvailabilityManager.cc
  SystemAvailabilityManager.hh
  SystemReports.cc
  SystemReports.hh
  SZVAVModel.cc
  SZVAVModel.hh
  TARCOGArgs.cc
  TARCOGArgs.hh
  TARCOGCommon.cc
  TARCOGCommon.hh
  TARCOGDeflection.cc
  TARCOGDeflection.hh
  TARCOGGasses90.cc
  TARCOGGasses90.hh
  TARCOGGassesParams.cc
  TARCOGGassesParams.hh
  TARCOGMain.cc
  TARCOGMain.hh
  TARCOGOutput.cc
  TARCOGOutput.hh
  TARCOGParams.cc
  TARCOGParams.hh
  TarcogShading.cc
  TarcogShading.hh
  ThermalChimney.cc
  ThermalChimney.hh
  ThermalComfort.cc
  ThermalComfort.hh
  ThermalEN673Calc.cc
  ThermalEN673Calc.hh
  ThermalISO15099Calc.cc
  ThermalISO15099Calc.hh
  Timer.h
  TranspiredCollector.cc
  TranspiredCollector.hh
  UFADManager.cc
  UFADManager.hh
  UnitHeater.cc
  UnitHeater.hh
  UnitVentilator.cc
  UnitVentilator.hh
  UserDefinedComponents.cc
  UserDefinedComponents.hh
  UtilityRoutines.cc
  UtilityRoutines.hh
  VariableSpeedCoils.cc
  VariableSpeedCoils.hh
  Vectors.cc
  Vectors.hh
  VentilatedSlab.cc
  VentilatedSlab.hh
  WaterCoils.cc
  WaterCoils.hh
  WaterManager.cc
  WaterManager.hh
  WaterThermalTanks.cc
  WaterThermalTanks.hh
  WaterToAirHeatPump.cc
  WaterToAirHeatPump.hh
  WaterToAirHeatPumpSimple.cc
  WaterToAirHeatPumpSimple.hh
  WaterUse.cc
  WaterUse.hh
  WeatherManager.cc
  WeatherManager.hh
  WindTurbine.cc
  WindTurbine.hh
  WindowAC.cc
  WindowAC.hh
  WindowComplexManager.cc
  WindowComplexManager.hh
  WindowEquivalentLayer.cc
  WindowEquivalentLayer.hh
  WindowManager.cc
  WindowManager.hh
  ZoneAirLoopEquipmentManager.cc
  ZoneAirLoopEquipmentManager.hh
  ZoneContaminantPredictorCorrector.cc
  ZoneContaminantPredictorCorrector.hh
  ZoneDehumidifier.cc
  ZoneDehumidifier.hh
  ZoneEquipmentManager.cc
  ZoneEquipmentManager.hh
  ZonePlenum.cc
  ZonePlenum.hh
  ZoneTempPredictorCorrector.cc
  ZoneTempPredictorCorrector.hh
)

CREATE_SRC_GROUPS( "${SRC}" )

if (UNIX)
  ADD_DEFINITIONS("-fPIC")
endif()

add_custom_target( GenerateEmbeddedEpJSONSchema
                   COMMAND ${CMAKE_COMMAND} -D "EnergyPlus_SOURCE_DIR:PATH=${CMAKE_CURRENT_SOURCE_DIR}"
                           -D "EnergyPlus_RUNTIME_OUTPUT_DIRECTORY:PATH=${CMAKE_RUNTIME_OUTPUT_DIRECTORY}"
                           -D "EnergyPlus_BINARY_DIR:PATH=${CMAKE_BINARY_DIR}"
                           -D "EnergyPlus_CURRENT_BINARY_DIR:PATH=${CMAKE_CURRENT_BINARY_DIR}"
                           -D "EnergyPlus_embeddable_epJSON_schema:PATH=$<TARGET_FILE:generate_embeddedable_epJSON_schema>"
                           -P "${CMAKE_SOURCE_DIR}/scripts/dev/generate_embeddable_epJSON_schema/generate_embedded_epJSON_schema.cmake"
                   WORKING_DIRECTORY ${CMAKE_BINARY_DIR}
                   DEPENDS generate_embeddedable_epJSON_schema )


# first we will create a static library of EnergyPlus
# this will be linked statically to create the DLL and also the unit tests
add_library( energypluslib STATIC ${SRC} )
target_link_libraries( energypluslib objexx sqlite bcvtb epexpat epfmiimport re2 DElight libkiva )
add_dependencies( energypluslib GenerateEmbeddedEpJSONSchema )
if(BUILD_GROUND_PLOT)
  set_source_files_properties(HeatBalanceKivaManager.cc PROPERTIES COMPILE_DEFINITIONS GROUND_PLOT)
  target_link_libraries( energypluslib groundplot )
endif()
if(UNIX AND NOT APPLE)
  target_link_libraries( energypluslib dl )
endif()
if (WIN32)
  target_link_libraries( energypluslib Shlwapi )
endif()

# second we will create the shared library that is actually packaged with EnergyPlus
add_library( energyplusapi SHARED  CommandLineInterface.hh CommandLineInterface.cc EnergyPlusPgm.cc public/EnergyPlusPgm.hh )
target_link_libraries( energyplusapi energypluslib )

set_target_properties(
  energyplusapi
  PROPERTIES
  INSTALL_NAME_DIR "@executable_path"
)
install( TARGETS energyplusapi
  RUNTIME DESTINATION ./
  LIBRARY DESTINATION ./
  ARCHIVE DESTINATION ./
)

if (MINGW)
  add_executable( energyplus main.cc  )
  target_link_libraries( energyplus energyplusapi )
elseif (CMAKE_COMPILER_IS_GNUCXX AND ENABLE_LTO)
  add_executable( energyplus main.cc  "EnergyPlusPgm.cc" "public/EnergyPlusPgm.hh" )
  target_link_libraries( energyplus energypluslib )
else()
  add_executable( energyplus main.cc  )
  target_link_libraries( energyplus energyplusapi )
endif()

set_target_properties(energyplus PROPERTIES VERSION ${ENERGYPLUS_VERSION})
set_target_properties(energyplusapi PROPERTIES VERSION ${ENERGYPLUS_VERSION})

install( TARGETS energyplus energyplusapi DESTINATION ./ )

if( BUILD_TESTING )
  # Build the test executable
  add_executable( TestEnergyPlusCallbacks test_ep_as_library.cc )
  target_link_libraries( TestEnergyPlusCallbacks energyplusapi )
  add_test(NAME "integration.TestEnergyPlusCallbacks"
           COMMAND ${CMAKE_COMMAND}
           -DSOURCE_DIR=${CMAKE_SOURCE_DIR}
           -DBINARY_DIR=${CMAKE_BINARY_DIR}
           -DIDF_FILE=1ZoneUncontrolled.idf
           -DEPW_FILE=USA_CO_Golden-NREL.724666_TMY3.epw
           -P ${CMAKE_SOURCE_DIR}/cmake/RunCallbackTest.cmake)
endif()

if(UNIX AND NOT APPLE)
  ADD_CUSTOM_COMMAND(TARGET energyplus POST_BUILD
  COMMAND ${CMAKE_COMMAND} -E create_symlink energyplus EnergyPlus
  COMMAND ${CMAKE_COMMAND} -E rename EnergyPlus "${CMAKE_BINARY_DIR}/Products/EnergyPlus")
endif()
