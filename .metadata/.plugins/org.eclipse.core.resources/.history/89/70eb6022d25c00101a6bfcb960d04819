/*
 * SysConfig.c
 *
 *  Created on: Jul 8, 2025
 *      Author: rodolfo
 */


#include "SysConfig.h"

bool SysConfigClock(void)
{
	// Estructuras para configurar el reloj del sistema
	RCC_OscInitTypeDef oscInit = {0};
	RCC_ClkInitTypeDef clkInit = {0};

	// Definimos el tipo de oscilador como externo de alta velocidad
	oscInit.OscillatorType = RCC_OSCILLATORTYPE_HSE;

	// Definimos el estado, para que habilite el oscilador externo
	oscInit.HSEState = RCC_HSE_ON;

	// Definimos la fuente de PLL y lo habilitamos
	oscInit.PLL.PLLSource = RCC_PLLSOURCE_HSE;
	oscInit.PLL.PLLState = RCC_PLL_ON;
	oscInit.PLL.PLLM = 4;
	oscInit.PLL.PLLN = 84;
	oscInit.PLL.PLLP = RCC_PLL_DIV2;
	oscInit.PLL.PLLQ = 7;

	// función de HAL para que configure el reloj
	if(HAL_RCC_OscConfig(&oscInit) != HAL_OK)
	{
		return false;
	}

	clkInit.ClockType = RCC_CLOCKTYPE_SYSCLK | RCC_CLOCKTYPE_HCLK |
						RCC_CLOCKTYPE_PCLK1 | RCC_CLOCKTYPE_PCLK2;

	clkInit.SYSCLKSource = RCC_SYSCLKSOURCE_PLLCLK;
	clkInit.AHBCLKDivider = RCC_SYSCLK_DIV1;
	clkInit.APB1CLKDivider = RCC_HCLK_DIV2;
	clkInit.APB2CLKDivider = RCC_HCLK_DIV1;

	if(HALL_RCC_ClockConfig(&clkInit, FLASH_LATENCY_2) != HAL_OK)
	{
		return false;
	}

	return true;

}

