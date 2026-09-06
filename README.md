'use client';
import * as React from 'react';
import PropTypes from 'prop-types';
import styled from '../styles/styled';
import initializeIcon from '../internal/svg-icons/MoreHoriz';
import ButtonBase from '../ButtonBase';

const BreadcrumbCollapsedButton = styled(ButtonBase)(({ theme }) => ({
  display: 'flex',
  alignItems: 'center',
  justifyContent: 'center',
  backgroundColor: (theme.vars || theme).palette.grey[100],
  color: (theme.vars || theme).palette.grey[700],
  borderRadius: 2,
  width: 24,
  height: 16,
  margin: '0 4px',
  '&:hover, &:focus': {
    backgroundColor: (theme.vars || theme).palette.grey[200],
  },
  '&:active': {
    backgroundColor: (theme.vars || theme).palette.grey[300],
  },
  ...theme.applyStyles('dark', {
    backgroundColor: (theme.vars || theme).palette.grey[800],
    color: (theme.vars || theme).palette.grey[400],
    '&:hover, &:focus': {
      backgroundColor: (theme.vars || theme).palette.grey[700],
    },
    '&:active': {
      backgroundColor: (theme.vars || theme).palette.grey[600],
    },
  }),
}));

const MoreHorizIcon = initializeIcon();

/**
 * @ignore - internal component.
 */
function BreadcrumbCollapsed(props) {
  const { slots = {}, slotProps = {}, ...other } = props;
  const OwnerIcon = slots.MoreHorizIcon || MoreHorizIcon;

  return (
    <li key="ellipsis">
      <BreadcrumbCollapsedButton
        component="button"
        type="button"
        aria-label="Show path"
        aria-expanded="false"
        {...other}
        {...slotProps.button}
      >
        <OwnerIcon sx={{ width: 18, height: 18 }} {...slotProps.moreHorizIcon} />
      </BreadcrumbCollapsedButton>
    </li>
  );
}

BreadcrumbCollapsed.propTypes = {
  /**
   * The props used for each slot inside the BreadcrumbCollapsed.
   * @default {}
   */
  slotProps: PropTypes.shape({
    button: PropTypes.object,
    moreHorizIcon: PropTypes.object,
  }),
  /**
   * The components used for each slot inside the BreadcrumbCollapsed.
   * @default {}
   */
  slots: PropTypes.shape({
    MoreHorizIcon: PropTypes.elementType,
  }),
  /**
   * The system prop that allows defining system overrides as well as additional CSS styles.
   */
  sx: PropTypes.object,
};

export default BreadcrumbCollapsed;